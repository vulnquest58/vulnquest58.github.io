---
layout: page
title: Writer - Hack The Box Writeup
subtitle: SQL Injection, SSRF via Image Upload and APT Hooks Abuse
permalink: /ctf/writeups/hackthebox/writer/
platform: hackthebox
machine_name: writer
difficulty: Medium
os: Linux
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: hackthebox
* **Name / Title**: writer
* **Difficulty**: Medium
* **Target OS / Environment**: Linux
* **Key Vulnerability Focus**: SQLi / SSRF / APT hook injection

---

### Exploitation Flow

1. **Reconnaissance**: SQLi in HTTP parameter allows dumping databases.
2. **Initial Foothold**: We find an administrative panel that fetches profile pictures via URL. We exploit SSRF to request local file resources, leak private keys, and SSH in.
3. **Privilege Escalation**: The user is a member of the pt group. We inject a custom malicious shell script into the APT update hooks: /etc/apt/apt.conf.d/. When APT update runs, our hook executes as root.
