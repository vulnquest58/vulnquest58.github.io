---
layout: page
title: "HateCTF - HTB Cyber Apocalypse 2025 Writeup"
subtitle: "PHP PHAR deserialization attack via a file manager. Upload a PHAR disguised as an image, trigger deserialization via a custom POP chain to achieve RCE."
permalink: /ctf/writeups/challenges/web/hatectf/
category: "web"
challenge_name: "HateCTF"
difficulty: "Hard"
event: "HTB Cyber Apocalypse 2025"
points: "482"
solves: "22"
date: 2026-06-26
---

## 🚩 Challenge Overview
* **Platform/Event**: HTB Cyber Apocalypse 2025
* **Difficulty**: Hard
* **Points**: 482
* **Solves**: 22
* **Category**: Web
* **Tags**: PHP Deserialization, PHAR, POP Chain, RCE

---

## 📝 Description
PHP PHAR deserialization attack via a file manager. Upload a PHAR disguised as an image, trigger deserialization via a custom POP chain to achieve RCE.

---

## 💡 Solution / Approach
1. Source review: `file_exists("phar://...")` call is reachable.

2. Build POP chain: `Logger::__destruct()` → `FileWriter::write()` → writes webshell.

3. Generate PHAR with forged GIF header: `GIF89a` prefix passes MIME check.

4. Upload file → trigger via `file_exists('phar://uploads/evil.gif/test')`.

5. Webshell dropped → RCE → flag at `/flag`.
