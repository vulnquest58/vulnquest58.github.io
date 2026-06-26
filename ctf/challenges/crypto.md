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

  <div class="challenge-card" data-year="2025" data-event="google">
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
    <div class="cc-solution">
      <details>
        <summary>View Approach</summary>
        <div class="cc-solution-body">
          <p>1. Identify weak parameters: Public exponent <code>e = 3</code> and ciphertext <code>c</code> is smaller than modulo <code>N</code> (meaning <code>m^3 < N</code>).</p>
          <p>2. The modulo arithmetic doesn't wrap around, so <code>c = m^3 mod N</code> simplifies to <code>c = m^3</code>.</p>
          <p>3. Calculate the exact integer cube root of `c` in Python to get `m` directly:</p>
          <pre><code>import gmpy2
from crypto.util.number import long_to_bytes

c = 12345... # ciphertext
m = gmpy2.iroot(c, 3)[0]
print(long_to_bytes(int(m)))</code></pre>
        </div>
      </details>
    </div>
  </div>

</div>

### HTB Cyber Apocalypse 2025

<div class="challenge-cards-list">

  <div class="challenge-card" data-year="2025" data-event="htb">
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
    <div class="cc-solution">
      <details>
        <summary>View Approach</summary>
        <div class="cc-solution-body">
          <p>1. Nonce reuse: Since <code>C_1 = P_1 ^ Keystream</code> and <code>C_2 = P_2 ^ Keystream</code>, then <code>C_1 ^ C_2 = P_1 ^ P_2</code>.</p>
          <p>2. We know <code>P_1</code> (a welcome message like "Hello Guest!"). We calculate the Keystream: <code>Keystream = C_1 ^ P_1</code>.</p>
          <p>3. Decrypt the flag ciphertext <code>C_flag</code> by XORing it with the recovered keystream: <code>P_flag = C_flag ^ Keystream</code>.</p>
        </div>
      </details>
    </div>
  </div>

</div>
