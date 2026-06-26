---
layout: page
title: Misc Hacking Challenges
subtitle: CTF miscellaneous & scripting challenge writeups by event and year
permalink: /ctf/challenges/misc/
---

<p class="page-lead">Miscellaneous, scripting, pyjails, and esoteric challenge writeups from Google CTF, DEF CON, picoCTF, and other global competitions. Organized by year and event.</p>

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
        <h4 class="cc-name">Jailbreak</h4>
      </div>
      <span class="cc-diff easy">Easy</span>
    </div>
    <div class="cc-body">
      <p><strong>Category</strong>: Misc · <strong>Points</strong>: 110 · <strong>Solves</strong>: 590</p>
      <p class="cc-desc">A Python PyJail interactive shell that blocks access to `import`, `os`, `sys`, and quotes. Escape the jail using subclasses references to read files.</p>
      <div class="cc-tags"><span>Python Jail</span><span>Sandbox Escape</span><span>Subclasses</span><span>Builtins</span></div>
    </div>
    <div class="cc-solution">
      <details>
        <summary>View Approach</summary>
        <div class="cc-solution-body">
          <p>1. The jail filters quotes, meaning we cannot use strings directly. We construct strings using <code>chr()</code> and <code>+</code>.</p>
          <p>2. Traverse subclasses from the base class: <code>().__class__.__base__.__subclasses__()</code>.</p>
          <p>3. Find the index of the <code>_frozen_importlib_external.FileFinder</code> or similar class that has access to system modules.</p>
          <p>4. Build payload using Python string formatting: <code>().__class__.__base__.__subclasses__()[137].__init__.__globals__[chr(115)+chr(121)+chr(115)].modules[chr(111)+chr(115)].system(chr(115)+chr(104))</code> to trigger a shell.</p>
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
        <h4 class="cc-name">Regex-Game</h4>
      </div>
      <span class="cc-diff medium">Medium</span>
    </div>
    <div class="cc-body">
      <p><strong>Category</strong>: Misc · <strong>Points</strong>: 230 · <strong>Solves</strong>: 290</p>
      <p class="cc-desc">Write a single regular expression under 40 characters that matches valid mathematical equations but rejects maliciously injection vectors.</p>
      <div class="cc-tags"><span>Regular Expressions</span><span>Input Validation</span><span>Constraints Bypass</span></div>
    </div>
    <div class="cc-solution">
      <details>
        <summary>View Approach</summary>
        <div class="cc-solution-body">
          <p>1. The validation script uses PHP's <code>preg_match</code> with a strict length count.</p>
          <p>2. The allowed characters are limited to numbers, arithmetic signs, and parentheses: <code>^[0-9+\-*\/()]+$</code>.</p>
          <p>3. To bypass the length check while preventing command injection via backticks or function calls, we use recursive subpatterns to match matching nesting parentheses: <code>^([0-9+\-*\/]|(\((?1)*\)))+$</code>.</p>
        </div>
      </details>
    </div>
  </div>

</div>
