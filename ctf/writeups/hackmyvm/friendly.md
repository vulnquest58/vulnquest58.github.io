---
layout: page
title: Friendly - HackMyVM Writeup
subtitle: Cewl wordlist generation, Hydra form bruteforcing, and SUID Find.
permalink: /ctf/writeups/hackmyvm/friendly/
platform: hackmyvm
machine_name: friendly
difficulty: Easy
os: Linux
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: hackmyvm
* **Name / Title**: friendly
* **Difficulty**: Easy
* **Target OS / Environment**: Linux
* **Key Vulnerability Focus**: Cewl wordlist / SUID find

---

### Walkthrough

1. **Foothold**: Use cewl to scrape words, run hydra to brute-force the web panel, upload a shell.
2. **Privilege Escalation**: SUID /usr/bin/find allows executing system commands as root.
