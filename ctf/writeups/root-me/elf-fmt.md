---
layout: page
title: ELF Format String - Root-Me Writeup
subtitle: Overwriting global variables in memory using printf %n format specifiers.
permalink: /ctf/writeups/root-me/elf-fmt/
platform: root-me
machine_name: elf-fmt
difficulty: Medium
os: Binary
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: root-me
* **Name / Title**: elf-fmt
* **Difficulty**: Medium
* **Target OS / Environment**: Binary
* **Key Vulnerability Focus**: Format String / %n memory overwrite

---

### Walkthrough

1. Find global variable memory address.
2. Inject a custom payload utilizing %n format specifier to overwrite the variable value in memory, triggering shell execution.
