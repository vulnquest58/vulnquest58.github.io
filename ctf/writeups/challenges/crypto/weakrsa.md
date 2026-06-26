---
layout: page
title: "WeakRSA - Google CTF 2025 Writeup"
subtitle: "RSA cryptosystem configured with a small public exponent (e=3). Perform a cube root attack on the ciphertext to decrypt the message without factoring N."
permalink: /ctf/writeups/challenges/crypto/weakrsa/
category: "crypto"
challenge_name: "WeakRSA"
difficulty: "Easy"
event: "Google CTF 2025"
points: "100"
solves: "610"
date: 2026-06-26
---

## 🚩 Challenge Overview
* **Platform/Event**: Google CTF 2025
* **Difficulty**: Easy
* **Points**: 100
* **Solves**: 610
* **Category**: Crypto
* **Tags**: RSA, Symmetric Crypto, Small Exponent, Cube Root

---

## 📝 Description
RSA cryptosystem configured with a small public exponent (e=3). Perform a cube root attack on the ciphertext to decrypt the message without factoring N.

---

## 💡 Solution / Approach
1. Identify weak parameters: Public exponent `e = 3` and ciphertext `c` is smaller than modulo `N` (meaning `m^3 < N`).

2. The modulo arithmetic doesn't wrap around, so `c = m^3 mod N` simplifies to `c = m^3`.

3. Calculate the exact integer cube root of `c` in Python to get `m` directly:

```python
import gmpy2
from crypto.util.number import long_to_bytes

c = 12345... # ciphertext
m = gmpy2.iroot(c, 3)[0]
print(long_to_bytes(int(m)))
```
