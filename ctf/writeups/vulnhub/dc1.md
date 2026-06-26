---
layout: page
title: DC-1 - VulnHub Writeup
subtitle: Drupalgeddon2 remote code execution and SUID Find privilege escalation.
permalink: /ctf/writeups/vulnhub/dc1/
platform: vulnhub
machine_name: dc1
difficulty: Easy
os: Linux
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: vulnhub
* **Name / Title**: dc1
* **Difficulty**: Easy
* **Target OS / Environment**: Linux
* **Key Vulnerability Focus**: Drupalgeddon2 / SUID find

---

### Walkthrough

1. **Foothold**: Exploit Drupal CMS via Drupalgeddon2 (CVE-2018-7600) using Metasploit to get a www-data shell.
2. **Privilege Escalation**: Locate SUID /usr/bin/find, run -exec /bin/sh \; to get root.
