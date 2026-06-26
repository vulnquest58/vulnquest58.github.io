---
layout: page
title: "Satellite - picoCTF 2025 Writeup"
subtitle: "Given a set of orbital parameters and a time window, find the name of the military vessel that passed closest to a specified research base."
permalink: /ctf/writeups/challenges/osint/satellite/
category: "osint"
challenge_name: "Satellite"
difficulty: "Medium"
event: "picoCTF 2025"
points: "180"
solves: "280"
date: 2026-06-26
---

## 🚩 Challenge Overview
* **Platform/Event**: picoCTF 2025
* **Difficulty**: Medium
* **Points**: 180
* **Solves**: 280
* **Category**: OSINT
* **Tags**: Satellite Tracking, Coordinate Analysis, OpenData, MarineTraffic

---

## 📝 Description
Given a set of orbital parameters and a time window, find the name of the military vessel that passed closest to a specified research base.

---

## 💡 Solution / Approach
1. Convert the satellite Two-Line Element (TLE) set into lat/long coordinates using a Python satellite tracking script (`pyephem` or `skyfield`).

2. Pinpoint the exact pass timestamp closest to the coordinates of the base (64.9°S, 63.5°W).

3. Use historical MarineTraffic or AIS vessel location portals to query ships active in the Antarctic Peninsula within that specific time window.

4. Identify the vessel: RRS Sir David Attenborough. The flag is the ship's MMSI number.
