---
layout: page
title: Blue - Hack The Box Writeup
subtitle: MS17-010 EternalBlue Windows SMBv1 Remote Code Execution
permalink: /ctf/writeups/hackthebox/blue/
platform: hackthebox
machine_name: blue
difficulty: Easy
os: Windows
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: hackthebox
* **Name / Title**: blue
* **Difficulty**: Easy
* **Target OS / Environment**: Windows
* **Key Vulnerability Focus**: EternalBlue / MS17-010

---

### Exploitation Flow

1. **Reconnaissance**: Port 445 (SMB) is open. Nmap script smb-vuln-ms17-010 confirms vulnerability.
2. **Initial Foothold**: We run Metasploit's exploit/windows/smb/ms17_010_eternalblue or use a Python implementation to exploit the pool corruption flaw in SMBv1, immediately returning a NT AUTHORITY\SYSTEM command shell.
