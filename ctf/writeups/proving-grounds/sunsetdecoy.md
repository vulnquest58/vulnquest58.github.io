---
layout: page
title: SunsetDecoy - Proving Grounds Writeup
subtitle: FTP anonymous logins, zip file password cracking, and SUID chroot.
permalink: /ctf/writeups/proving-grounds/sunsetdecoy/
platform: proving-grounds
machine_name: sunsetdecoy
difficulty: Easy
os: Linux
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: proving-grounds
* **Name / Title**: sunsetdecoy
* **Difficulty**: Easy
* **Target OS / Environment**: Linux
* **Key Vulnerability Focus**: Zip cracking / SUID chroot

---

### Walkthrough

1. **Foothold**: Download ackup.zip via FTP, crack zip password using John, extract SSH keys.
2. **Privilege Escalation**: SUID /usr/sbin/chroot allows executing commands as root.
