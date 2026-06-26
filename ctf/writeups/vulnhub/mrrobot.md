---
layout: page
title: Mr. Robot - VulnHub Writeup
subtitle: WordPress username bruteforce, SUID Nmap privilege escalation, and key carving.
permalink: /ctf/writeups/vulnhub/mrrobot/
platform: vulnhub
machine_name: mrrobot
difficulty: Easy
os: Linux
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: vulnhub
* **Name / Title**: mrrobot
* **Difficulty**: Easy
* **Target OS / Environment**: Linux
* **Key Vulnerability Focus**: WordPress exploit / SUID Nmap

---

### Walkthrough

1. **Web Enum**: Gobuster yields /wp-login.php.
2. **Initial Foothold**: Brute-force WordPress username and passwords, upload a PHP reverse shell.
3. **Privilege Escalation**: Locate SUID 
map binary, trigger interactive mode (
map --interactive), and run !sh to get root.
