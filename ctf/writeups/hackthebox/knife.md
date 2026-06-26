---
layout: page
title: Knife - Hack The Box Writeup
subtitle: PHP 8.1.0-dev Backdoor User-Agent RCE to Root via Sudo Knife
permalink: /ctf/writeups/hackthebox/knife/
platform: hackthebox
machine_name: knife
difficulty: Easy
os: Linux
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: hackthebox
* **Name / Title**: knife
* **Difficulty**: Easy
* **Target OS / Environment**: Linux
* **Key Vulnerability Focus**: PHP backdoor (CVE-2021-3129) / Sudo knife SUID

---

### Exploitation Flow

1. **Reconnaissance**: Nmap scan reveals port 22 and 80 open.
2. **Initial Foothold**: Inspecting HTTP headers reveals the server runs PHP/8.1.0-dev. This specific development version has an easter-egg backdoor that executes shell commands passed in the User-Agentt header:
   `ash
   curl -s -H "User-Agentt: zerodium system('id');" http://10.10.10.242/
   # Returns: uid=1000(james)
   `
3. **Privilege Escalation**: Checking sudo -l reveals that james can run /usr/bin/knife as root:
   `ash
   sudo knife exec -E 'exec "/bin/sh"'
   # Spawns: root shell
   `
"@

Create-Writeup "hackthebox" "nibbles" "Nibbles - Hack The Box Writeup" "File Upload Vulnerability in Nibbleblog CMS and Sudo Wildcard Shell Script Escapes" "Easy" "Linux" "File upload RCE / Sudo script wildcard injection" @"
### Exploitation Flow

1. **Reconnaissance**: Port 80 is open, serving an under-construction page. Brute-forcing directory yields /nibbleblog/.
2. **Initial Foothold**: Log into Nibbleblog admin using default credentials (dmin:nibbles). Upload a PHP reverse shell via the "My Image" plugin, which does not sanitize file extensions.
3. **Privilege Escalation**: We find a writable shell script /home/nibbler/personal/stuff/monitor.sh that user 
ibbler can run as root via sudo. We append /bin/sh to the script and execute it to escalate to root.
