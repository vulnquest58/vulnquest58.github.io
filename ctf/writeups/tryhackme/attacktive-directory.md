---
layout: page
title: Attacktive Directory - TryHackMe Writeup
subtitle: Kerberos enumeration, AS-REP Roasting, and secrets dumping on a Windows domain controller.
permalink: /ctf/writeups/tryhackme/attacktive-directory/
platform: tryhackme
machine_name: attacktive-directory
difficulty: Medium
os: AD
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: tryhackme
* **Name / Title**: attacktive-directory
* **Difficulty**: Medium
* **Target OS / Environment**: AD
* **Key Vulnerability Focus**: AS-REP Roasting / User enum / secretsdump

---

### Walkthrough

1. **Enumeration**: Kerberos username enumeration via Kerbrute.
2. **AS-REP Roasting**: Retrieve TGT hash for svc_default user and crack it using John.
3. **Takeover**: Relaying credentials and dumping hashes using secretsdump.py.
