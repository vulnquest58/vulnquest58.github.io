---
layout: page
title: Gift - HackMyVM Writeup
subtitle: Active Directory Certificate Services Relay and GPO abuse.
permalink: /ctf/writeups/hackmyvm/gift/
platform: hackmyvm
machine_name: gift
difficulty: Hard
os: Windows
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: hackmyvm
* **Name / Title**: gift
* **Difficulty**: Hard
* **Target OS / Environment**: Windows
* **Key Vulnerability Focus**: ADCS relay / GPO abuse

---

### Walkthrough

1. **Foothold**: Exploit NTLM relaying against AD CS enrollment.
2. **Privilege Escalation**: Relayout Group Policies to escalate local user to Domain Admin.
