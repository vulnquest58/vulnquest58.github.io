---
layout: page
title: PwnLab: init - VulnHub Writeup
subtitle: LFI log poisoning, upload extension bypass, and SUID exploitation.
permalink: /ctf/writeups/vulnhub/pwnlab/
platform: vulnhub
machine_name: pwnlab
difficulty: Hard
os: Linux
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: vulnhub
* **Name / Title**: pwnlab
* **Difficulty**: Hard
* **Target OS / Environment**: Linux
* **Key Vulnerability Focus**: LFI / upload bypass / SUID

---

### Walkthrough

1. **Web**: Local File Inclusion (LFI) allows reading PHP source codes.
2. **Foothold**: Bypass file upload checks, trigger execution via LFI.
3. **Privilege Escalation**: Run SUID binary that calls a system command without absolute path, hijack PATH environment variable to execute our malicious script as root.
