---
layout: page
title: BountyHunter - Hack The Box Writeup
subtitle: XXE Injection in XML Form Parser and Python Eval Input Injection
permalink: /ctf/writeups/hackthebox/bountyhunter/
platform: hackthebox
machine_name: bountyhunter
difficulty: Medium
os: Linux
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: hackthebox
* **Name / Title**: bountyhunter
* **Difficulty**: Medium
* **Target OS / Environment**: Linux
* **Key Vulnerability Focus**: XXE / Python eval() code injection

---

### Exploitation Flow

1. **Reconnaissance**: Port 80 hosts a bounty tracker page. Submitting a ticket triggers an XML POST request.
2. **Initial Foothold**: The XML parser is vulnerable to XML External Entity (XXE) injection. We use it to read local system configuration files and locate user credentials in database files.
3. **Privilege Escalation**: The user can execute a custom Python script as root via sudo. The script uses eval() on raw input parameters. We inject Python payload __import__('os').system('/bin/bash') through the parameter to spawn a root shell.
