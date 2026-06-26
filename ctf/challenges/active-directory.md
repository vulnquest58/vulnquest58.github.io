---
layout: page
title: Active Directory Attacks
subtitle: Active Directory and network-level attack writeups by event and year
permalink: /ctf/challenges/active-directory/
---
<p class="page-lead">Active Directory, LDAP, Kerberos, and internal network hacking writeups from global enterprise CTFs and ProLabs. Organized by year and event.</p>
<div class="challenge-year-nav">
<button class="mf-btn active" data-filter="all">All Years</button>
<button class="mf-btn" data-filter="2025">2025</button>
<button class="mf-btn" data-filter="2024">2024</button>
</div>

---

## 2025 Challenges

### HTB Cyber Apocalypse 2025

<div class="challenge-cards-list">
<div class="challenge-card" data-event="htb" data-year="2025">
<div class="cc-header">
<div class="cc-title-area">
<span class="cc-event-badge htb">HTB Cyber Apocalypse 2025</span>
<h4 class="cc-name">ESC-Relay</h4>
</div>
<span class="cc-diff hard">Hard</span>
</div>
<div class="cc-body">
<p><strong>Category</strong>: Active Directory · <strong>Points</strong>: 480 · <strong>Solves</strong>: 34</p>
<p class="cc-desc">Exploit AD CS ESC8 vulnerability. Coerce HTTP NTLM authentication from a domain controller using MS-RPRN Printer Bug, and relay it to the AD CS Web Enrollment endpoint to request a Domain Admin certificate.</p>
<div class="cc-tags"><span>AD CS</span><span>ESC8</span><span>NTLM Relaying</span><span>Printer Bug</span><span>Coercion</span></div>
</div>
<div class="cc-solution"><a class="cc-btn" href="{{ '/ctf/writeups/challenges/active-directory/esc-relay/' | relative_url }}">Writeup →</a></div>
</div>
</div>

### DEF CON 2024 Quals

<div class="challenge-cards-list">
<div class="challenge-card" data-event="defcon" data-year="2024">
<div class="cc-header">
<div class="cc-title-area">
<span class="cc-event-badge defcon">DEF CON 2024 Quals</span>
<h4 class="cc-name">Kerberoast-Showdown</h4>
</div>
<span class="cc-diff medium">Medium</span>
</div>
<div class="cc-body">
<p><strong>Category</strong>: Active Directory · <strong>Points</strong>: 300 · <strong>Solves</strong>: 110</p>
<p class="cc-desc">Read Active Directory SPNs without domain credentials by abusing unauthenticated LDAP queries, then execute Kerberoasting against target service accounts.</p>
<div class="cc-tags"><span>Kerberoasting</span><span>LDAP Query</span><span>SPN</span><span>Impacket</span></div>
</div>
<div class="cc-solution"><a class="cc-btn" href="{{ '/ctf/writeups/challenges/active-directory/kerberoast-showdown/' | relative_url }}">Writeup →</a></div>
</div>
</div>
