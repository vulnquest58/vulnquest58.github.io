---
layout: page
title: Kioptrix Level 1 - VulnHub Writeup
subtitle: Exploiting vulnerable OpenSSL version via remote overflow code to root.
permalink: /ctf/writeups/vulnhub/kioptrix/
platform: vulnhub
machine_name: kioptrix
difficulty: Easy
os: Linux
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: vulnhub
* **Name / Title**: kioptrix
* **Difficulty**: Easy
* **Target OS / Environment**: Linux
* **Key Vulnerability Focus**: OpenSSL buffer overflow

---

### Walkthrough

1. **Enum**: Nmap reveals Samba and Apache (mod_ssl).
2. **Foothold**: Compile and run the OpenFuck exploit targeting the vulnerable OpenSSL/mod_ssl version, immediately granting a root shell.
