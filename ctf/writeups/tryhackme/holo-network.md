---
layout: page
title: Holo Network - TryHackMe Writeup
subtitle: Complete network compromise: initial foothold, lateral movement, pivoting, and AD forest takeover.
permalink: /ctf/writeups/tryhackme/holo-network/
platform: tryhackme
machine_name: holo-network
difficulty: Hard
os: Network
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: tryhackme
* **Name / Title**: holo-network
* **Difficulty**: Hard
* **Target OS / Environment**: Network
* **Key Vulnerability Focus**: Pivoting / Network compromises

---

### Walkthrough Summary

1. **Initial Access**: Vulnerable web app leads to a shell.
2. **Local Privesc**: Abuse of SUID binary to escalate to root.
3. **Pivoting**: Tunneling local ports using Chisel to reach internal network subnets.
4. **Active Directory Domain Compromise**: Performing Kerberoasting and abusing local administrative rights to take over the Domain Controller.
