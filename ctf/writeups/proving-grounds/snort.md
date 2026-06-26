---
layout: page
title: Snort - Proving Grounds Writeup
subtitle: Snort Admin console remote stack buffer overflow exploit.
permalink: /ctf/writeups/proving-grounds/snort/
platform: proving-grounds
machine_name: snort
difficulty: Medium
os: Windows
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: proving-grounds
* **Name / Title**: snort
* **Difficulty**: Medium
* **Target OS / Environment**: Windows
* **Key Vulnerability Focus**: Remote Buffer Overflow / Assembly JMP ESP

---

### Walkthrough

1. **Exploitation**: Exploit vulnerable Snort monitoring console by hijacking EIP with JMP ESP pointer.
2. **Privilege Escalation**: The shell returns NT AUTHORITY\SYSTEM context directly.
