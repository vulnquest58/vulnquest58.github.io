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
<div class="challenge-card" data-event="google" data-year="2025">
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
<div class="cc-solution"><a class="cc-btn" href="{{ '/ctf/writeups/challenges/pwn/ret2win/' | relative_url }}">Writeup →</a></div>
</div>
</div>

### HTB Cyber Apocalypse 2025

<div class="challenge-cards-list">
<div class="challenge-card" data-event="htb" data-year="2025">
<div class="cc-header">
<div class="cc-title-area">
<span class="cc-event-badge htb">HTB Cyber Apocalypse 2025</span>
<h4 class="cc-name">Chatbot</h4>
</div>
<span class="cc-diff medium">Medium</span>
</div>
<div class="cc-body">
<p><strong>Category</strong>: Pwn · <strong>Points</strong>: 280 · <strong>Solves</strong>: 145</p>
<p class="cc-desc">A console chatbot vulnerable to format strings and stack overflows. Leak stack values (canary &amp; libc addresses) via format string, then trigger stack overflow to perform a ret2libc payload.</p>
<div class="cc-tags"><span>Format String</span><span>Stack Canary Bypass</span><span>ret2libc</span><span>ASLR Bypass</span></div>
</div>
<div class="cc-solution"><a class="cc-btn" href="{{ '/ctf/writeups/challenges/pwn/chatbot/' | relative_url }}">Writeup →</a></div>
</div>
</div>
