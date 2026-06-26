---
layout: page
title: "FlagChecker - Google CTF 2025 Writeup"
subtitle: "A simple C++ binary that validates user input character-by-character using nested math equations. Extract the equations to calculate the flag."
permalink: /ctf/writeups/challenges/reversing/flagchecker/
category: "reversing"
challenge_name: "FlagChecker"
difficulty: "Easy"
event: "Google CTF 2025"
points: "110"
solves: "541"
date: 2026-06-26
---

## 🚩 Challenge Overview
* **Platform/Event**: Google CTF 2025
* **Difficulty**: Easy
* **Points**: 110
* **Solves**: 541
* **Category**: Reversing
* **Tags**: ELF x64, Static Analysis, Equation Solving, Z3 Solver

---

## 📝 Description
A simple C++ binary that validates user input character-by-character using nested math equations. Extract the equations to calculate the flag.

---

## 💡 Solution / Approach
1. Open binary in IDA Pro. Locate the flag verification loop.

2. The code performs linear transformations: `(input[i] ^ key[i]) + 5 == target[i]`.

3. Extract arrays `key` and `target` from data section.

4. Write a simple Python Z3 script to solve the equations and rebuild the flag.
