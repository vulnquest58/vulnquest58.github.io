---
layout: page
title: "AES-Leak - HTB Cyber Apocalypse 2025 Writeup"
subtitle: "AES-CTR mode encryption reusing the same nonce/IV across different messages. Recover the keystream and decrypt the flag."
permalink: /ctf/writeups/challenges/crypto/aes-leak/
category: "crypto"
challenge_name: "AES-Leak"
difficulty: "Medium"
event: "HTB Cyber Apocalypse 2025"
points: "250"
solves: "198"
date: 2026-06-26
---

## 🚩 Challenge Overview
* **Platform/Event**: HTB Cyber Apocalypse 2025
* **Difficulty**: Medium
* **Points**: 250
* **Solves**: 198
* **Category**: Crypto
* **Tags**: AES-CTR, Nonce Reuse, Keystream Recovery, Known Plaintext

---

## 📝 Description
AES-CTR mode encryption reusing the same nonce/IV across different messages. Recover the keystream and decrypt the flag.

---

## 💡 Solution / Approach
1. Nonce reuse: Since `C_1 = P_1 ^ Keystream` and `C_2 = P_2 ^ Keystream`, then `C_1 ^ C_2 = P_1 ^ P_2`.

2. We know `P_1` (a welcome message like "Hello Guest!"). We calculate the Keystream: `Keystream = C_1 ^ P_1`.

3. Decrypt the flag ciphertext `C_flag` by XORing it with the recovered keystream: `P_flag = C_flag ^ Keystream`.
