---
layout: page
title: "PacketMonster - Google CTF 2025 Writeup"
subtitle: "A network PCAP file containing suspicious port scanning and TCP streams. Locate the payload transmission stream and carve out the hidden files."
permalink: /ctf/writeups/challenges/forensics/packetmonster/
category: "forensics"
challenge_name: "PacketMonster"
difficulty: "Easy"
event: "Google CTF 2025"
points: "100"
solves: "580"
date: 2026-06-26
---

## 🚩 Challenge Overview
* **Platform/Event**: Google CTF 2025
* **Difficulty**: Easy
* **Points**: 100
* **Solves**: 580
* **Category**: Forensics
* **Tags**: PCAP, Wireshark, TCP Stream, File Carving

---

## 📝 Description
A network PCAP file containing suspicious port scanning and TCP streams. Locate the payload transmission stream and carve out the hidden files.

---

## 💡 Solution / Approach
1. Open the PCAP file in Wireshark. Filter by `http` or `tcp.port == 80` to isolate web traffic.

2. Locate a large POST request transferring binary data: stream index 14.

3. Right-click, select "Follow TCP Stream", view data as "Raw", and click "Save as..." to save it as `transfer.bin`.

4. Run `binwalk -e transfer.bin` to unpack the zipped file containing the flag.
