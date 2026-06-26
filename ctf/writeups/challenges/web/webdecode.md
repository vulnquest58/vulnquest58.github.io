---
layout: page
title: "WebDecode - picoCTF 2024 Writeup"
subtitle: "Flag hidden as a Base64-encoded data- attribute in the HTML source. Inspect → decode → flag."
permalink: /ctf/writeups/challenges/web/webdecode/
category: "web"
challenge_name: "WebDecode"
difficulty: "Easy"
event: "picoCTF 2024"
points: "100"
solves: "8,421"
date: 2026-06-26
---

## 🚩 Challenge Overview
* **Platform/Event**: picoCTF 2024
* **Difficulty**: Easy
* **Points**: 100
* **Solves**: 8,421
* **Category**: Web
* **Tags**: Source Review, Base64

---

## 📝 Description
Flag hidden as a Base64-encoded data- attribute in the HTML source. Inspect → decode → flag.

---

## 💡 Solution / Approach
```python
curl -s http://target/ | grep 'data-' | base64 -d
```
