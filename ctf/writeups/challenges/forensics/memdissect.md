---
layout: page
title: "MemDissect - HTB Cyber Apocalypse 2025 Writeup"
subtitle: "Memory dump of a Windows Server compromised via LSASS dumping. Use Volatility 3 to locate the LSASS process and recover NT hashes."
permalink: /ctf/writeups/challenges/forensics/memdissect/
category: "forensics"
challenge_name: "MemDissect"
difficulty: "Medium"
event: "HTB Cyber Apocalypse 2025"
points: "260"
solves: "140"
date: 2026-06-26
---

## 🚩 Challenge Overview
* **Platform/Event**: HTB Cyber Apocalypse 2025
* **Difficulty**: Medium
* **Points**: 260
* **Solves**: 140
* **Category**: Forensics
* **Tags**: Volatility 3, Memory Forensics, LSASS, Credential Dumping

---

## 📝 Description
Memory dump of a Windows Server compromised via LSASS dumping. Use Volatility 3 to locate the LSASS process and recover NT hashes.

---

## 💡 Solution / Approach
1. Run Volatility info plugin to identify the OS: `python3 vol.py -f mem.raw windows.info`.

2. List active processes to confirm lsass.exe was dumped: `windows.pslist`.

3. Dump credentials using the hashdump plugin: `python3 vol.py -f mem.raw windows.hashdump.Hashdump`.

4. Crack the administrator hash using John or Hashcat to find the secret passphrase flag.
