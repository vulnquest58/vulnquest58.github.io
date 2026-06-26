---
layout: page
title: Horizontall - Hack The Box Writeup
subtitle: Strapi CMS RCE and Local Laravel Telemetry SSRF to Root
permalink: /ctf/writeups/hackthebox/horizontall/
platform: hackthebox
machine_name: horizontall
difficulty: Medium
os: Linux
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: hackthebox
* **Name / Title**: horizontall
* **Difficulty**: Medium
* **Target OS / Environment**: Linux
* **Key Vulnerability Focus**: Strapi CMS RCE / Laravel telemetry port pivoting

---

### Exploitation Flow

1. **Reconnaissance**: Scan reveals Strapi CMS v3.0.0-beta.17.4 running on subdomain.
2. **Initial Foothold**: We exploit unauthenticated Password Reset Password Leak & RCE vulnerability (CVE-2019-19609) in Strapi to execute shell commands and receive a reverse shell.
3. **Privilege Escalation**: Local port 8000 hosts a Laravel application with Telemetry features enabled. We pivot and send an exploit command to the local Laravel interface to trigger unserialize RCE, spawning a root shell.
