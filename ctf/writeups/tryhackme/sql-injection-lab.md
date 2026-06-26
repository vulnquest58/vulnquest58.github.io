---
layout: page
title: SQL Injection Lab - TryHackMe Writeup
subtitle: Union-based, blind boolean, and time-based SQL injection exploitation notes.
permalink: /ctf/writeups/tryhackme/sql-injection-lab/
platform: tryhackme
machine_name: sql-injection-lab
difficulty: Medium
os: Web
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: tryhackme
* **Name / Title**: sql-injection-lab
* **Difficulty**: Medium
* **Target OS / Environment**: Web
* **Key Vulnerability Focus**: SQL Injection / Blind boolean / Time-based

---

### Exploit Methods

* **Union-Based**: Merging database tables to extract data directly.
* **Blind Boolean**: Querying the database with true/false conditions to deduce characters by page changes.
* **Time-Based**: Using timing functions (like sleep()) to verify database queries bit-by-bit.
