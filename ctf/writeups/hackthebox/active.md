---
layout: page
title: Active - Hack The Box Writeup
subtitle: Group Policy Preferences Decryption and Kerberoasting Domain Administrator
permalink: /ctf/writeups/hackthebox/active/
platform: hackthebox
machine_name: active
difficulty: Hard
os: Windows
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: hackthebox
* **Name / Title**: active
* **Difficulty**: Hard
* **Target OS / Environment**: Windows
* **Key Vulnerability Focus**: GPP decryption / Kerberoasting

---

### Exploitation Flow

1. **Reconnaissance**: SMB null session allows downloading GPO files.
2. **Initial Foothold**: We decrypt the domain user SVC_TGS password from the GPO XML file Groups.xml using the public Microsoft GPP key (gpp-decrypt).
3. **Privilege Escalation**: Using SVC_TGS credentials, we run Kerberoasting to request a Service ticket (TGS) for the Administrator account SPN. Cracking the ticket offline yields the Domain Admin password.
