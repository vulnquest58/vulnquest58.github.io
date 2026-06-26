---
layout: page
title: "Chatbot - HTB Cyber Apocalypse 2025 Writeup"
subtitle: "A console chatbot vulnerable to format strings and stack overflows. Leak stack values (canary & libc addresses) via format string, then trigger stack overflow to perform a ret2libc payload."
permalink: /ctf/writeups/challenges/pwn/chatbot/
category: "pwn"
challenge_name: "Chatbot"
difficulty: "Medium"
event: "HTB Cyber Apocalypse 2025"
points: "280"
solves: "145"
date: 2026-06-26
---

## 🚩 Challenge Overview
* **Platform/Event**: HTB Cyber Apocalypse 2025
* **Difficulty**: Medium
* **Points**: 280
* **Solves**: 145
* **Category**: Pwn
* **Tags**: Format String, Stack Canary Bypass, ret2libc, ASLR Bypass

---

## 📝 Description
A console chatbot vulnerable to format strings and stack overflows. Leak stack values (canary & libc addresses) via format string, then trigger stack overflow to perform a ret2libc payload.

---

## 💡 Solution / Approach
1. Format string leak: Inject `%11$p.%15$p` to leak stack canary and `__libc_start_main_ret` address.

2. Calculate libc base and offset to `system()` and `/bin/sh`.

3. Send stack overflow payload: Fill buffer, place leaked canary, overwrite RBP, and write ROP chain (`pop rdi; pop rsi; system`) pointing to `/bin/sh`.
