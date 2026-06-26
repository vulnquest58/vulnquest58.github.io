---
layout: page
title: Compromising AD - TryHackMe Notes
subtitle: Abusing Active Directory services, Kerberos authentication protocol, and lateral movement methods.
permalink: /ctf/writeups/tryhackme/compromising-active-directory/
platform: tryhackme
machine_name: compromising-active-directory
difficulty: Hard
os: AD
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: tryhackme
* **Name / Title**: compromising-active-directory
* **Difficulty**: Hard
* **Target OS / Environment**: AD
* **Key Vulnerability Focus**: Kerberoasting / AS-REP roasting / lateral movement / BloodHound

---

### Active Directory Exploits

* **Kerberoasting**: Requesting service tickets (TGS) for accounts with Service Principal Names (SPN) and cracking their hashes offline.
* **AS-REP Roasting**: Fetching ticket-granting ticket (TGT) hashes for accounts with Kerberos pre-authentication disabled.
* **BloodHound**: Visualizing Active Directory permission graphs to locate structural trust vulnerabilities.
