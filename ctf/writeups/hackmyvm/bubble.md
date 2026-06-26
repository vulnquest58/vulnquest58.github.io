---
layout: page
title: Bubble - HackMyVM Writeup
subtitle: Apache log poisoning LFI, local port forwarding, and Jenkins Script Console RCE.
permalink: /ctf/writeups/hackmyvm/bubble/
platform: hackmyvm
machine_name: bubble
difficulty: Medium
os: Linux
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: hackmyvm
* **Name / Title**: bubble
* **Difficulty**: Medium
* **Target OS / Environment**: Linux
* **Key Vulnerability Focus**: Log poisoning / Local port forward / Jenkins console

---

### Walkthrough

1. **Foothold**: Poison Apache access logs, trigger shell via LFI.
2. **Privilege Escalation**: Tunnel local port 8080. Access Jenkins Admin Console, execute Groovy shell script to spawn a root shell.
