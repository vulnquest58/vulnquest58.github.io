---
layout: page
title: Legacy - Hack The Box Writeup
subtitle: MS08-067 Windows SMB Service Stack Buffer Overflow
permalink: /ctf/writeups/hackthebox/legacy/
platform: hackthebox
machine_name: legacy
difficulty: Easy
os: Windows
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: hackthebox
* **Name / Title**: legacy
* **Difficulty**: Easy
* **Target OS / Environment**: Windows
* **Key Vulnerability Focus**: MS08-067 / Remote Buffer Overflow

---

### Exploitation Flow

1. **Reconnaissance**: Port 445 is open on a legacy Windows XP machine.
2. **Initial Foothold**: The host is vulnerable to MS08-067. We compile a python exploit containing shellcode to hijack the SMB NetAPI stack buffer. Executing the exploit spawns a shell as local admin.
