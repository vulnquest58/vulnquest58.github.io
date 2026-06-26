---
layout: page
title: Cryptography
subtitle: CTF cryptography challenge writeups by event and year
permalink: /ctf/challenges/crypto/
---
<p class="page-lead">Cryptography writeups from Google CTF, DEF CON, picoCTF, and other global competitions. Organized by year and event.</p>
<div class="challenge-year-nav">
<button class="mf-btn active" data-filter="all">All Years</button>
<button class="mf-btn" data-filter="2025">2025</button>
<button class="mf-btn" data-filter="2024">2024</button>
</div>

---

## 2025 Challenges

### Google CTF 2025

<div class="challenge-cards-list">
<div class="challenge-card" data-event="google" data-year="2025">
<div class="cc-header">
<div class="cc-title-area">
<span class="cc-event-badge google">Google CTF 2025</span>
<h4 class="cc-name">WeakRSA</h4>
</div>
<span class="cc-diff easy">Easy</span>
</div>
<div class="cc-body">
<p><strong>Category</strong>: Crypto · <strong>Points</strong>: 100 · <strong>Solves</strong>: 610</p>
<p class="cc-desc">RSA cryptosystem configured with a small public exponent (e=3). Perform a cube root attack on the ciphertext to decrypt the message without factoring N.</p>
<div class="cc-tags"><span>RSA</span><span>Symmetric Crypto</span><span>Small Exponent</span><span>Cube Root</span></div>
</div>
<div class="cc-solution"><a class="cc-btn" href="{{ '/ctf/writeups/challenges/crypto/weakrsa/' | relative_url }}">Writeup →</a></div>
</div>
</div>

### HTB Cyber Apocalypse 2025

<div class="challenge-cards-list">
<div class="challenge-card" data-event="htb" data-year="2025">
<div class="cc-header">
<div class="cc-title-area">
<span class="cc-event-badge htb">HTB Cyber Apocalypse 2025</span>
<h4 class="cc-name">AES-Leak</h4>
</div>
<span class="cc-diff medium">Medium</span>
</div>
<div class="cc-body">
<p><strong>Category</strong>: Crypto · <strong>Points</strong>: 250 · <strong>Solves</strong>: 198</p>
<p class="cc-desc">AES-CTR mode encryption reusing the same nonce/IV across different messages. Recover the keystream and decrypt the flag.</p>
<div class="cc-tags"><span>AES-CTR</span><span>Nonce Reuse</span><span>Keystream Recovery</span><span>Known Plaintext</span></div>
</div>
<div class="cc-solution"><a class="cc-btn" href="{{ '/ctf/writeups/challenges/crypto/aes-leak/' | relative_url }}">Writeup →</a></div>
</div>
</div>
