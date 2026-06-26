---
layout: page
title: SQLi Filter Bypass - Root-Me Writeup
subtitle: Bypassing quote filters using Hexadecimal encodings.
permalink: /ctf/writeups/root-me/sqli-bypass/
platform: root-me
machine_name: sqli-bypass
difficulty: Easy
os: Web
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: root-me
* **Name / Title**: sqli-bypass
* **Difficulty**: Easy
* **Target OS / Environment**: Web
* **Key Vulnerability Focus**: SQLi quotes bypass

---

### Walkthrough

1. Perform UNION SQL injection on numeric inputs.
2. Bypass table string name filters by converting queries to Hex representation.
