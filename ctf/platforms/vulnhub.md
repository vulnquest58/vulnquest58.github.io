---
layout: page
title: VulnHub Writeups
subtitle: Offline vulnerable VMs for OSCP preparation and pentesting practice
permalink: /ctf/platforms/vulnhub/
---

<div class="platform-hero vh-hero">
  <div class="plat-hero-icon">💽</div>
  <div class="plat-hero-text">
    <h2>VulnHub</h2>
    <p>Downloadable offline VMs — perfect for network-level pentesting, OSCP prep, and practicing without internet-connected environments.</p>
    <div class="plat-hero-badges">
      <span class="badge badge-warning">OSCP Prep</span>
      <span class="badge badge-info">25+ VMs</span>
      <span class="badge badge-dark">Offline</span>
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

## Machine List

<div class="machines-list">

  <div class="machine-card" data-os="linux" data-diff="easy">
    <div class="mc-left"><span class="mc-os linux">🐧</span><div><h4 class="mc-name">Mr. Robot</h4><span class="mc-ip">DHCP</span></div></div>
    <div class="mc-mid"><span class="mc-tech">WordPress brute-force → reverse shell → SUID nmap → root</span></div>
    <div class="mc-right"><span class="mc-diff easy">Easy</span><a href="{{ '/ctf/writeups/vulnhub/mrrobot/' | relative_url }}" class="mc-btn">Writeup →</a></div>
  </div>

  <div class="machine-card" data-os="linux" data-diff="easy">
    <div class="mc-left"><span class="mc-os linux">🐧</span><div><h4 class="mc-name">Kioptrix Level 1</h4><span class="mc-ip">DHCP</span></div></div>
    <div class="mc-mid"><span class="mc-tech">OpenSSL 0.9.6 exploit (ptrace-kmod) · remote buffer overflow → root</span></div>
    <div class="mc-right"><span class="mc-diff easy">Easy</span><a href="{{ '/ctf/writeups/vulnhub/kioptrix/' | relative_url }}" class="mc-btn">Writeup →</a></div>
  </div>

  <div class="machine-card" data-os="linux" data-diff="easy">
    <div class="mc-left"><span class="mc-os linux">🐧</span><div><h4 class="mc-name">DC-1</h4><span class="mc-ip">DHCP</span></div></div>
    <div class="mc-mid"><span class="mc-tech">Drupalgeddon2 (CVE-2018-7600) → SUID find → root</span></div>
    <div class="mc-right"><span class="mc-diff easy">Easy</span><a href="{{ '/ctf/writeups/vulnhub/dc1/' | relative_url }}" class="mc-btn">Writeup →</a></div>
  </div>

  <div class="machine-card" data-os="linux" data-diff="medium">
    <div class="mc-left"><span class="mc-os linux">🐧</span><div><h4 class="mc-name">HackLAB: Vulnix</h4><span class="mc-ip">DHCP</span></div></div>
    <div class="mc-mid"><span class="mc-tech">NFS root squash bypass → SSH key injection → sudo su</span></div>
    <div class="mc-right"><span class="mc-diff medium">Medium</span><a href="{{ '/ctf/writeups/vulnhub/vulnix/' | relative_url }}" class="mc-btn">Writeup →</a></div>
  </div>

  <div class="machine-card" data-os="linux" data-diff="medium">
    <div class="mc-left"><span class="mc-os linux">🐧</span><div><h4 class="mc-name">SkyTower</h4><span class="mc-ip">DHCP</span></div></div>
    <div class="mc-mid"><span class="mc-tech">SQL injection in login → SSH through proxy → multiple privesc steps</span></div>
    <div class="mc-right"><span class="mc-diff medium">Medium</span><a href="{{ '/ctf/writeups/vulnhub/skytower/' | relative_url }}" class="mc-btn">Writeup →</a></div>
  </div>

  <div class="machine-card" data-os="linux" data-diff="hard">
    <div class="mc-left"><span class="mc-os linux">🐧</span><div><h4 class="mc-name">PwnLab: init</h4><span class="mc-ip">DHCP</span></div></div>
    <div class="mc-mid"><span class="mc-tech">PHP LFI → log poisoning → file upload bypass → SUID binary privesc</span></div>
    <div class="mc-right"><span class="mc-diff hard">Hard</span><a href="{{ '/ctf/writeups/vulnhub/pwnlab/' | relative_url }}" class="mc-btn">Writeup →</a></div>
  </div>

  <div class="machine-card" data-os="linux" data-diff="hard">
    <div class="mc-left"><span class="mc-os linux">🐧</span><div><h4 class="mc-name">Raven 2</h4><span class="mc-ip">DHCP</span></div></div>
    <div class="mc-mid"><span class="mc-tech">PHPMailer RCE (CVE-2016-10033) → MySQL UDF root exploitation</span></div>
    <div class="mc-right"><span class="mc-diff hard">Hard</span><a href="{{ '/ctf/writeups/vulnhub/raven2/' | relative_url }}" class="mc-btn">Writeup →</a></div>
  </div>

</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
  document.querySelectorAll('.mf-btn').forEach(btn => {
    btn.addEventListener('click', function() {
      const filter = this.dataset.filter;
      document.querySelectorAll('.mf-btn').forEach(b => b.classList.remove('active'));
      this.classList.add('active');
      document.querySelectorAll('.machine-card').forEach(card => {
        card.style.display = (filter === 'all' || card.dataset.diff === filter) ? 'flex' : 'none';
      });
    });
  });
});
</script>
