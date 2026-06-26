---
layout: page
title: "WhereIsIt - Google CTF 2025 Writeup"
subtitle: "Identify the exact name of a building visible in a cropped image featuring a reflective glass facade. Locate the coordinates and find the town name."
permalink: /ctf/writeups/challenges/osint/whereisit/
category: "osint"
challenge_name: "WhereIsIt"
difficulty: "Easy"
event: "Google CTF 2025"
points: "100"
solves: "630"
date: 2026-06-26
---

## 🚩 Challenge Overview
* **Platform/Event**: Google CTF 2025
* **Difficulty**: Easy
* **Points**: 100
* **Solves**: 630
* **Category**: OSINT
* **Tags**: Geolocation, Image Reverse Search, Reflections

---

## 📝 Description
Identify the exact name of a building visible in a cropped image featuring a reflective glass facade. Locate the coordinates and find the town name.

---

## 💡 Solution / Approach
1. Crop the reflection in the window showing a distinctive bridge tower shape.

2. Reverse search the bridge on Google Images / Yandex: identifies it as the Vasco da Gama Bridge in Lisbon, Portugal.

3. Use Google Maps 3D view from the Lisbon waterfront to align the building's reflection angles with nearby office blocks.

4. Locate the exact office: Myriad by Sana Hotels. The flag is the postal code of the building.
