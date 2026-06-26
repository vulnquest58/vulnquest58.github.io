---
layout: page
title: Throwback Network - TryHackMe Writeup
subtitle: Multi-host enterprise Active Directory forest simulation with firewall pivots and domain trust exploitation.
permalink: /ctf/writeups/tryhackme/throwback-network/
platform: tryhackme
machine_name: throwback-network
difficulty: Hard
os: Network
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: tryhackme
* **Name / Title**: throwback-network
* **Difficulty**: Hard
* **Target OS / Environment**: Network
* **Key Vulnerability Focus**: Corporate network emulation / pivoting

---

### Walkthrough Summary

1. **Phishing & Initial Access**: Compromising a public-facing workstation.
2. **Internal Pivoting**: Deploying reverse tunnels and pivot agents to scan the internal corporate domain.
3. **Active Directory Takeover**: Exploiting weak group policies (GPP) and DCSync rights to compromise the child and forest root domains.
