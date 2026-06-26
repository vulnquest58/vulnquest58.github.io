---
layout: page
title: Offshore ProLab - Hack The Box Writeup
subtitle: Active Directory Forest Trusts and AD CS Certificate Abuse Escalation
permalink: /ctf/writeups/hackthebox/offshore/
platform: hackthebox
machine_name: offshore
difficulty: Insane
os: Windows
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: hackthebox
* **Name / Title**: offshore
* **Difficulty**: Insane
* **Target OS / Environment**: Windows
* **Key Vulnerability Focus**: ADCS ESC1 / Forest Trust exploitation

---

### Exploitation Flow

1. **Reconnaissance**: Multi-domain Active Directory forest assessment.
2. **Initial Access**: Internal network pivot via compromised client machine.
3. **Privilege Escalation**: Identify vulnerable Active Directory Certificate Services (AD CS) template configured with ESC1 (allows requesting certificates for arbitrary users). We request a certificate as Domain Admin.
