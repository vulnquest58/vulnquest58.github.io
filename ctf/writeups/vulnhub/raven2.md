---
layout: page
title: Raven 2 - VulnHub Writeup
subtitle: PHPMailer RCE (CVE-2016-10033) and MySQL UDF Privilege Escalation.
permalink: /ctf/writeups/vulnhub/raven2/
platform: vulnhub
machine_name: raven2
difficulty: Hard
os: Linux
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: vulnhub
* **Name / Title**: raven2
* **Difficulty**: Hard
* **Target OS / Environment**: Linux
* **Key Vulnerability Focus**: PHPMailer RCE / MySQL UDF

---

### Walkthrough

1. **Foothold**: Exploit PHPMailer RCE (CVE-2016-10033) to write a backdoor shell in the web folder.
2. **Privilege Escalation**: The MySQL database runs as root and allows writing plugins. Write a custom User Defined Function (UDF) library and execute system commands as root.
