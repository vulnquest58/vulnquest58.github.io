---
layout: page
title: SkyTower - VulnHub Writeup
subtitle: SQL Injection login bypass and SSH port tunneling.
permalink: /ctf/writeups/vulnhub/skytower/
platform: vulnhub
machine_name: skytower
difficulty: Medium
os: Linux
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: vulnhub
* **Name / Title**: skytower
* **Difficulty**: Medium
* **Target OS / Environment**: Linux
* **Key Vulnerability Focus**: SQLi / SSH tunneling

---

### Walkthrough

1. **Web Enum**: SQL Injection in the login panel bypasses authentication.
2. **Foothold**: Obtain credentials, SSH in (which is blocked by TCP wrappers unless tunneled). Pivot using SSH tunnel options.
