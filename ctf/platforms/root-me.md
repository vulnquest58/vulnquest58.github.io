---
layout: page
title: Root-Me
subtitle: Diverse CTF challenges across multiple disciplines
permalink: /ctf/platforms/root-me/
---

<div class="platform-hero rm-hero">
  <div class="plat-hero-icon">🌱</div>
  <div class="plat-hero-text">
    <h2>Root-Me</h2>
    <p>A comprehensive French CTF platform offering hundreds of hacking challenges spanning web, systems, forensics, cryptology, and network security.</p>
    <div class="plat-hero-badges">
      <span class="badge badge-dark">Rank: Top 1000</span>
      <span class="badge badge-info">80+ Solves</span>
      <span class="badge badge-success">4000+ Points</span>
    </div>
  </div>
</div>

<div class="machine-filter-bar">
  <button class="mf-btn active" data-filter="all">All</button>
  <button class="mf-btn" data-filter="easy">Easy</button>
  <button class="mf-btn" data-filter="medium">Medium</button>
  <button class="mf-btn" data-filter="hard">Hard</button>
</div>

---

## Challenge List

<div class="machines-list">

  <div class="machine-card" data-os="web" data-diff="easy">
    <div class="mc-left"><span class="mc-os web">🌐</span><div><h4 class="mc-name">SQL Injection - Filter Bypass</h4><span class="mc-ip">Web-Server</span></div></div>
    <div class="mc-mid"><span class="mc-tech">Bypassing quote/slash sanitization · hex conversion of queries · database dump</span></div>
    <div class="mc-right"><span class="mc-diff easy">Easy</span><a href="{{ '/ctf/writeups/root-me/sqli-bypass/' | relative_url }}" class="mc-btn">Writeup →</a></div>
  </div>

  <div class="machine-card" data-os="linux" data-diff="medium">
    <div class="mc-left"><span class="mc-os linux">🐧</span><div><h4 class="mc-name">ELF Format String - Basic</h4><span class="mc-ip">App-System</span></div></div>
    <div class="mc-mid"><span class="mc-tech">Overwriting global variable value in memory via printf() vulnerability · shell spawn</span></div>
    <div class="mc-right"><span class="mc-diff medium">Medium</span><a href="{{ '/ctf/writeups/root-me/elf-fmt/' | relative_url }}" class="mc-btn">Writeup →</a></div>
  </div>

</div>

---


<script>
document.addEventListener('DOMContentLoaded', function() {
  const filterBtns = document.querySelectorAll('.machine-filter-bar .mf-btn');
  const machineCards = document.querySelectorAll('.machine-card');
  filterBtns.forEach(btn => {
    btn.addEventListener('click', function() {
      const filter = this.dataset.filter;
      filterBtns.forEach(b => b.classList.remove('active'));
      this.classList.add('active');
      machineCards.forEach(card => {
        if (filter === 'all' || card.dataset.os === filter || card.dataset.diff === filter) {
          card.style.display = 'flex';
        } else {
          card.style.display = 'none';
        }
      });
    });
  });
});
</script>
