---
layout: page
title: "Transformer - picoCTF 2025 Writeup"
subtitle: "Obfuscated Python bytecode (.pyc). Decompile, analyze custom execution VM structure, and reverse the state mutations to retrieve the original input."
permalink: /ctf/writeups/challenges/reversing/transformer/
category: "reversing"
challenge_name: "Transformer"
difficulty: "Medium"
event: "picoCTF 2025"
points: "200"
solves: "310"
date: 2026-06-26
---

## 🚩 Challenge Overview
* **Platform/Event**: picoCTF 2025
* **Difficulty**: Medium
* **Points**: 200
* **Solves**: 310
* **Category**: Reversing
* **Tags**: Python VM, Bytecode Decompilation, uncompyle6, VM Analysis

---

## 📝 Description
Obfuscated Python bytecode (.pyc). Decompile, analyze custom execution VM structure, and reverse the state mutations to retrieve the original input.

---

## 💡 Solution / Approach
1. Use `pycdc` or `uncompyle6` to decompile the Python bytecode back into source code.

2. Analyze the custom VM interpreter loop: it has instructions like ADD, XOR, ROTATE on a 16-byte state.

3. Re-implement each VM instruction in reverse order to undo the state transitions, starting with the final state hardcoded in the file.
