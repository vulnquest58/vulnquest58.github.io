---
layout: page
title: Reverse Engineering
subtitle: CTF reverse engineering challenge writeups by event and year
permalink: /ctf/challenges/reversing/
---
<p class="page-lead">Reverse engineering writeups from Google CTF, DEF CON, picoCTF, and other global competitions. Organized by year and event.</p>
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
<h4 class="cc-name">FlagChecker</h4>
</div>
<span class="cc-diff easy">Easy</span>
</div>
<div class="cc-body">
<p><strong>Category</strong>: Reversing · <strong>Points</strong>: 110 · <strong>Solves</strong>: 541</p>
<p class="cc-desc">A simple C++ binary that validates user input character-by-character using nested math equations. Extract the equations to calculate the flag.</p>
<div class="cc-tags"><span>ELF x64</span><span>Static Analysis</span><span>Equation Solving</span><span>Z3 Solver</span></div>
</div>
<div class="cc-solution"><a class="cc-btn" href="{{ '/ctf/writeups/challenges/reversing/flagchecker/' | relative_url }}">Writeup →</a></div>
</div>
</div>

### picoCTF 2025

<div class="challenge-cards-list">
<div class="challenge-card" data-event="pico" data-year="2025">
<div class="cc-header">
<div class="cc-title-area">
<span class="cc-event-badge pico">picoCTF 2025</span>
<h4 class="cc-name">Transformer</h4>
</div>
<span class="cc-diff medium">Medium</span>
</div>
<div class="cc-body">
<p><strong>Category</strong>: Reversing · <strong>Points</strong>: 200 · <strong>Solves</strong>: 310</p>
<p class="cc-desc">Obfuscated Python bytecode (.pyc). Decompile, analyze custom execution VM structure, and reverse the state mutations to retrieve the original input.</p>
<div class="cc-tags"><span>Python VM</span><span>Bytecode Decompilation</span><span>uncompyle6</span><span>VM Analysis</span></div>
</div>
<div class="cc-solution"><a class="cc-btn" href="{{ '/ctf/writeups/challenges/reversing/transformer/' | relative_url }}">Writeup →</a></div>
</div>
</div>
