---
layout: page
title: HackMyVM
subtitle: Community-built vulnerable Linux and Windows machines
permalink: /ctf/platforms/hackmyvm/
---

<div class="platform-hero hmv-hero">
  <div class="plat-hero-icon">🎮</div>
  <div class="plat-hero-text">
    <h2>HackMyVM</h2>
    <p>A community-driven hacking platform featuring custom-built machines designed to test lateral thinking and enumeration.</p>
    <div class="plat-hero-badges">
      <span class="badge badge-success">Rank: Top 50</span>
      <span class="badge badge-info">20+ VMs Solved</span>
      <span class="badge badge-warning">Active Contributor</span>
    </div>
  </div>
</div>

<div class="machine-filter-bar">
  <button class="mf-btn active" data-filter="all">All</button>
  <button class="mf-btn" data-filter="linux">🐧 Linux</button>
  <button class="mf-btn" data-filter="windows">🪟 Windows</button>
  <button class="mf-btn" data-filter="easy">Easy</button>
  <button class="mf-btn" data-filter="medium">Medium</button>
  <button class="mf-btn" data-filter="hard">Hard</button>
</div>

---

## Machine List

<div class="machines-list">

  <div class="machine-card" data-os="linux" data-diff="easy">
    <div class="mc-left"><span class="mc-os linux">🐧</span><div><h4 class="mc-name">Friendly</h4><span class="mc-ip">DHCP</span></div></div>
    <div class="mc-mid"><span class="mc-tech">Port 80 HTTP enum · wordlist generation via cewl · SUID binary exploit</span></div>
    <div class="mc-right"><span class="mc-diff easy">Easy</span><a href="{{ '/ctf/writeups/hackmyvm/friendly/' | relative_url }}" class="mc-btn">Writeup →</a></div>
  </div>

  <div class="machine-card" data-os="linux" data-diff="medium">
    <div class="mc-left"><span class="mc-os linux">🐧</span><div><h4 class="mc-name">Bubble</h4><span class="mc-ip">DHCP</span></div></div>
    <div class="mc-mid"><span class="mc-tech">Apache Log Injection LFI → reverse shell · local port forward · root exploit</span></div>
    <div class="mc-right"><span class="mc-diff medium">Medium</span><a href="{{ '/ctf/writeups/hackmyvm/bubble/' | relative_url }}" class="mc-btn">Writeup →</a></div>
  </div>

  <div class="machine-card" data-os="windows" data-diff="hard">
    <div class="mc-left"><span class="mc-os windows">🪟</span><div><h4 class="mc-name">Gift</h4><span class="mc-ip">DHCP</span></div></div>
    <div class="mc-mid"><span class="mc-tech">SMB null session → user enumeration · AD CS certificate relay · GPO path</span></div>
    <div class="mc-right"><span class="mc-diff hard">Hard</span><a href="{{ '/ctf/writeups/hackmyvm/gift/' | relative_url }}" class="mc-btn">Writeup →</a></div>
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
