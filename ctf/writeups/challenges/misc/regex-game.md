---
layout: page
title: "Regex-Game - HTB Cyber Apocalypse 2025 Writeup"
subtitle: "Write a single regular expression under 40 characters that matches valid mathematical equations but rejects maliciously injection vectors."
permalink: /ctf/writeups/challenges/misc/regex-game/
category: "misc"
challenge_name: "Regex-Game"
difficulty: "Medium"
event: "HTB Cyber Apocalypse 2025"
points: "230"
solves: "290"
date: 2026-06-26
---

## 🚩 Challenge Overview
* **Platform/Event**: HTB Cyber Apocalypse 2025
* **Difficulty**: Medium
* **Points**: 230
* **Solves**: 290
* **Category**: Misc
* **Tags**: Regular Expressions, Input Validation, Constraints Bypass

---

## 📝 Description
Write a single regular expression under 40 characters that matches valid mathematical equations but rejects maliciously injection vectors.

---

## 💡 Solution / Approach
1. The validation script uses PHP's `preg_match` with a strict length count.

2. The allowed characters are limited to numbers, arithmetic signs, and parentheses: `^[0-9+\-*\/()]+$`.

3. To bypass the length check while preventing command injection via backticks or function calls, we use recursive subpatterns to match matching nesting parentheses: `^([0-9+\-*\/]|(\((?1)*\)))+$`.
