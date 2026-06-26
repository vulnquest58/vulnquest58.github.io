---
layout: page
title: Mantis - Hack The Box Writeup
subtitle: MSSQL SQL Injection and MS14-068 Kerberos PAC Forgery Attack
permalink: /ctf/writeups/hackthebox/mantis/
platform: hackthebox
machine_name: mantis
difficulty: Hard
os: Windows
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: hackthebox
* **Name / Title**: mantis
* **Difficulty**: Hard
* **Target OS / Environment**: Windows
* **Key Vulnerability Focus**: MSSQL Injection / MS14-068 PAC forgery

---

### Exploitation Flow

1. **Reconnaissance**: SQL Injection in an IIS database client allows reading local configuration files.
2. **Initial Foothold**: We log in to the MSSQL instance, enable xp_cmdshell, and spawn a shell as sql_svc.
3. **Privilege Escalation**: The DC is vulnerable to MS14-068 (Kerberos PAC validation flaw). We generate a forged Kerberos ticket using goldenPac.py to authenticate as Domain Admin.
