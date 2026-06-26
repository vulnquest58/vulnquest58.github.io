---
layout: page
title: CTF Hub
subtitle: Platforms, Machines & Challenge Writeups
description: "Complete CTF hub — lab platforms with machine writeups, challenge categories by type and event, and web vulnerability reference guides."
---

<div class="ctf-hub-grid">

  <a href="{{ '/ctf/platforms/' | relative_url }}" class="ctf-hub-card platforms-card">
    <div class="hub-card-icon">🖥️</div>
    <div class="hub-card-body">
      <h2>Lab Platforms</h2>
      <p>Machines, rooms & writeups from HackTheBox, TryHackMe, VulnHub, HackMyVM, Proving Grounds, PentesterLab, and more.</p>
      <div class="hub-card-stats">
        <span><strong>8</strong> Platforms</span>
        <span><strong>200+</strong> Machines</span>
        <span><strong>Linux · Windows · AD</strong></span>
      </div>
      <span class="hub-card-cta">Browse Machines →</span>
    </div>
  </a>

  <a href="{{ '/ctf/challenges/' | relative_url }}" class="ctf-hub-card challenges-card">
    <div class="hub-card-icon">🚩</div>
    <div class="hub-card-body">
      <h2>CTF Challenges</h2>
      <p>Writeups organized by challenge type — Web, Pwn, Reversing, Crypto, Forensics, OSINT, Misc — from DEF CON, Google CTF, picoCTF, and global events.</p>
      <div class="hub-card-stats">
        <span><strong>8</strong> Categories</span>
        <span><strong>300+</strong> Challenges</span>
        <span><strong>Multi-year</strong></span>
      </div>
      <span class="hub-card-cta">Browse Challenges →</span>
    </div>
  </a>

  <a href="{{ '/ctf/web-vulnerabilities/' | relative_url }}" class="ctf-hub-card vuln-card">
    <div class="hub-card-icon">🌐</div>
    <div class="hub-card-body">
      <h2>Web Vulnerability Reference</h2>
      <p>OWASP Top 10 deep dives, PortSwigger Academy labs, advanced web attack techniques, and curated learning paths for web security mastery.</p>
      <div class="hub-card-stats">
        <span><strong>OWASP Top 10</strong></span>
        <span><strong>PortSwigger</strong></span>
        <span><strong>150+ Labs</strong></span>
      </div>
      <span class="hub-card-cta">Explore Vulnerabilities →</span>
    </div>
  </a>

</div>

---

## 📊 Quick Stats

<div class="ctf-quick-stats">
  <div class="qs-item"><div class="qs-num">Pro Hacker</div><div class="qs-label">HTB Rank</div></div>
  <div class="qs-item"><div class="qs-num">Top 1%</div><div class="qs-label">THM Rank</div></div>
  <div class="qs-item"><div class="qs-num">Expert</div><div class="qs-label">PortSwigger Level</div></div>
  <div class="qs-item"><div class="qs-num">40+</div><div class="qs-label">HTB Machines</div></div>
  <div class="qs-item"><div class="qs-num">120+</div><div class="qs-label">THM Rooms</div></div>
  <div class="qs-item"><div class="qs-num">150+</div><div class="qs-label">PS Labs</div></div>
</div>

---

## 🏆 Recent Writeups

{% assign all_writeups = site.pages | where_exp: "p", "p.path contains 'ctf/'" | sort: 'date' | reverse %}
{% for p in all_writeups limit: 6 %}
  {% if p.machine_name %}
  <div class="recent-writeup-card">
    <span class="rw-platform">{{ p.platform }}</span>
    <span class="rw-name">{{ p.machine_name }}</span>
    <span class="rw-level rw-{{ p.difficulty | downcase }}">{{ p.difficulty }}</span>
    <span class="rw-os">{{ p.os }}</span>
    <a href="{{ p.url | relative_url }}">Read →</a>
  </div>
  {% endif %}
{% endfor %}
