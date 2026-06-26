---
layout: page
title: Brutus - Hack The Box Writeup
subtitle: SSH Bruteforce Log Analysis and Digital Forensics
permalink: /ctf/writeups/hackthebox/brutus/
platform: hackthebox
machine_name: brutus
difficulty: Easy
os: Linux
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: hackthebox
* **Name / Title**: brutus
* **Difficulty**: Easy
* **Target OS / Environment**: Linux
* **Key Vulnerability Focus**: Log analysis / Forensics

---

### Analysis Flow

1. **Incident**: The client reports an unauthorized SSH login.
2. **Analysis**: We inspect /var/log/auth.log and identify over 5000 failed SSH login attempts from IP 192.168.1.100 targeting user cyber.
3. **Resolution**: Locate the successful login event, trace the execution of SUID commands, and identify the backdoor user account added by the attacker.
