---
layout: page
title: Sauna - Hack The Box Writeup
subtitle: AS-REP Roasting and Domain Controller DCSync Privileges Abuse
permalink: /ctf/writeups/hackthebox/sauna/
platform: hackthebox
machine_name: sauna
difficulty: Medium
os: Windows
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: hackthebox
* **Name / Title**: sauna
* **Difficulty**: Medium
* **Target OS / Environment**: Windows
* **Key Vulnerability Focus**: AS-REP Roasting / DCSync domain compromise

---

### Exploitation Flow

1. **Reconnaissance**: Gather names from the website. Build usernames list.
2. **Initial Foothold**: AS-REP Roasting yields user hsmith hash. Cracking it gives WinRM access.
3. **Privilege Escalation**: We find autologon registry keys containing the password for svc_backup. Logging in as svc_backup shows it has the GetChangesAll privilege. We execute DCSync to dump Administrator hashes.
