---
layout: page
title: OhSINT - TryHackMe Writeup
subtitle: OSINT investigation: EXIF data extraction, reverse image searching, and username tracking.
permalink: /ctf/writeups/tryhackme/ohsint/
platform: tryhackme
machine_name: ohsint
difficulty: Easy
os: OSINT
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: tryhackme
* **Name / Title**: ohsint
* **Difficulty**: Easy
* **Target OS / Environment**: OSINT
* **Key Vulnerability Focus**: Image EXIF metadata / Username footprinting

---

### OSINT Process

1. Extract EXIF data from target image using exiftool to find GPS coordinates.
2. Use Google Dorking on the discovered username to locate social media profiles.
3. Locate the flag hidden in the source code of a personal blogging page.
