---
layout: page
title: Proving Grounds
subtitle: OffSec's official OSCP practice environment
permalink: /ctf/platforms/proving-grounds/
---

<div class="platform-hero pg-hero">
  <div class="plat-hero-icon">🎯</div>
  <div class="plat-hero-text">
    <h2>Proving Grounds</h2>
    <p>OffSec's dedicated platform featuring a mix of community and OffSec-developed machines that replicate the OSCP exam environment.</p>
    <div class="plat-hero-badges">
      <span class="badge badge-danger">OSCP Practice</span>
      <span class="badge badge-info">30+ Machines Owned</span>
      <span class="badge badge-success">Passed OSCP</span>
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
    <div class="mc-left"><span class="mc-os linux">🐧</span><div><h4 class="mc-name">SunsetDecoy</h4><span class="mc-ip">192.168.x.x</span></div></div>
    <div class="mc-mid"><span class="mc-tech">FTP anonymous access · shadow backup zip file · john cracking · sudo chroot</span></div>
    <div class="mc-right"><span class="mc-diff easy">Easy</span><a href="{{ '/ctf/writeups/proving-grounds/sunsetdecoy/' | relative_url }}" class="mc-btn">Writeup →</a></div>
  </div>

  <div class="machine-card" data-os="windows" data-diff="medium">
    <div class="mc-left"><span class="mc-os windows">🪟</span><div><h4 class="mc-name">Snort</h4><span class="mc-ip">192.168.x.x</span></div></div>
    <div class="mc-mid"><span class="mc-tech">Vulnerable Snort service · remote stack buffer overflow · MSFVenom shellcode</span></div>
    <div class="mc-right"><span class="mc-diff medium">Medium</span><a href="{{ '/ctf/writeups/proving-grounds/snort/' | relative_url }}" class="mc-btn">Writeup →</a></div>
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
