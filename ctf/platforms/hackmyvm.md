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
      <span class="badge badge-success">Rank: #77 Global</span>
      <span class="badge badge-info">1,214 Points · [WTF]</span>
      <span class="badge badge-warning">104 Machines Rooted</span>
    </div>
  </div>
</div>

<div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(130px,1fr));gap:0.6rem;margin:1rem 0 1.5rem;">
  <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.75rem;text-align:center;">
    <div style="font-size:1.6rem;font-weight:800;color:#4ade80;font-family:var(--font-mono);">104</div>
    <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.05em;margin-top:2px;">Total Roots</div>
  </div>
  <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.75rem;text-align:center;">
    <div style="font-size:1.6rem;font-weight:800;color:#93c5fd;font-family:var(--font-mono);">103</div>
    <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.05em;margin-top:2px;">Total Users</div>
  </div>
  <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.75rem;text-align:center;">
    <div style="font-size:1.6rem;font-weight:800;color:#f87171;font-family:var(--font-mono);">3</div>
    <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.05em;margin-top:2px;">First Roots 🩸</div>
  </div>
  <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.75rem;text-align:center;">
    <div style="font-size:1.6rem;font-weight:800;color:#fbbf24;font-family:var(--font-mono);">1</div>
    <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.05em;margin-top:2px;">First User 🩸</div>
  </div>
  <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.75rem;text-align:center;">
    <div style="font-size:1.6rem;font-weight:800;color:#a78bfa;font-family:var(--font-mono);">9</div>
    <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.05em;margin-top:2px;">Challenges</div>
  </div>
  <div style="background:rgba(255,255,255,0.03);border:1px solid var(--border-color);border-radius:8px;padding:0.75rem;text-align:center;">
    <div style="font-size:1.6rem;font-weight:800;color:#4ade80;font-family:var(--font-mono);">#77</div>
    <div style="font-size:0.7rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.05em;margin-top:2px;">Global Rank</div>
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
