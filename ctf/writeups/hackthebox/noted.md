---
layout: page
title: Noted - Hack The Box Writeup
subtitle: Volatility Memory Forensics and Credential Dumping
permalink: /ctf/writeups/hackthebox/noted/
platform: hackthebox
machine_name: noted
difficulty: Medium
os: Windows
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: hackthebox
* **Name / Title**: noted
* **Difficulty**: Medium
* **Target OS / Environment**: Windows
* **Key Vulnerability Focus**: Volatility 3 / Memory Forensics

---

### Analysis Flow

1. **Incident**: System compromise reported on a core database node.
2. **Memory Analysis**: We download the memory dump dump.raw and run Volatility 3.
3. **Resolution**: Run windows.pslist to view processes, locate the PID of lsass.exe, dump memory, and parse the credentials of the logged-in administrator to identify the compromised account.
