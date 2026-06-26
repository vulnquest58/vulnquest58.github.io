---
layout: page
title: HackLAB: Vulnix - VulnHub Writeup
subtitle: Abusing NFS exports root squash configurations and injecting SSH keys.
permalink: /ctf/writeups/vulnhub/vulnix/
platform: vulnhub
machine_name: vulnix
difficulty: Medium
os: Linux
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: vulnhub
* **Name / Title**: vulnix
* **Difficulty**: Medium
* **Target OS / Environment**: Linux
* **Key Vulnerability Focus**: NFS root squash / SSH key injection

---

### Walkthrough

1. **Enum**: Nmap finds port 2049 (NFS).
2. **Initial Foothold**: Mount NFS export share locally, notice root squashing is off on /home/vulnix. Inject our public SSH key into uthorized_keys file.
3. **Privilege Escalation**: SSH as the user, execute local exploits to escalate to root.
