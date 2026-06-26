---
layout: page
title: TryHackMe
subtitle: Rooms, paths and standalone attack writeups
permalink: /ctf/platforms/tryhackme/
---

<div class="platform-hero thm-hero">
  <div class="plat-hero-icon">🏫</div>
  <div class="plat-hero-text">
    <h2>TryHackMe</h2>
    <p>Guided learning rooms, red team attack paths, advanced standalone rooms, and SOC analyst training.</p>
    <div class="plat-hero-badges">
      <span class="badge badge-success">Rank: Top 1%</span>
      <span class="badge badge-info">120+ Rooms</span>
      <span class="badge badge-warning">15+ Badges</span>
    </div>
  </div>
</div>

<div class="machine-filter-bar">
  <button class="mf-btn active" data-filter="all">All</button>
  <button class="mf-btn" data-filter="easy">Easy</button>
  <button class="mf-btn" data-filter="medium">Medium</button>
  <button class="mf-btn" data-filter="hard">Hard</button>
  <button class="mf-btn" data-filter="redteam">🔴 Red Team</button>
  <button class="mf-btn" data-filter="web">🌐 Web</button>
  <button class="mf-btn" data-filter="ad">🏢 Active Directory</button>
  <button class="mf-btn" data-filter="forensics">🔬 Forensics</button>
  <button class="mf-btn" data-filter="osint">🕵️ OSINT</button>
</div>

---

## 🔴 Red Team Path Rooms

<div class="machines-list">

  <div class="machine-card" data-os="redteam" data-diff="medium">
    <div class="mc-left"><span class="mc-os redteam">🔴</span><div><h4 class="mc-name">Red Team Fundamentals</h4><span class="mc-ip">Path — Room 1</span></div></div>
    <div class="mc-mid"><span class="mc-tech">Red team structure · threat intelligence · OPSEC · C2 fundamentals</span></div>
    <div class="mc-right"><span class="mc-diff medium">Medium</span><a href="#rtf" class="mc-btn">Notes ↓</a></div>
  </div>

  <div class="machine-card" data-os="redteam" data-diff="medium">
    <div class="mc-left"><span class="mc-os redteam">🔴</span><div><h4 class="mc-name">Red Team Engagements</h4><span class="mc-ip">Path — Room 2</span></div></div>
    <div class="mc-mid"><span class="mc-tech">Scoping, rules of engagement, mission planning, reporting templates</span></div>
    <div class="mc-right"><span class="mc-diff medium">Medium</span><a href="#rte" class="mc-btn">Notes ↓</a></div>
  </div>

  <div class="machine-card" data-os="redteam" data-diff="hard">
    <div class="mc-left"><span class="mc-os redteam">🔴</span><div><h4 class="mc-name">Compromising Active Directory</h4><span class="mc-ip">Standalone</span></div></div>
    <div class="mc-mid"><span class="mc-tech">Kerberoasting · AS-REP · LDAP enum · BloodHound · lateral movement</span></div>
    <div class="mc-right"><span class="mc-diff hard">Hard</span><a href="#comp-ad" class="mc-btn">Notes ↓</a></div>
  </div>

  <div class="machine-card" data-os="redteam" data-diff="hard">
    <div class="mc-left"><span class="mc-os redteam">🔴</span><div><h4 class="mc-name">Holo Network</h4><span class="mc-ip">Network Lab</span></div></div>
    <div class="mc-mid"><span class="mc-tech">Full red team op: initial access → C2 → pivoting → AD domain takeover</span></div>
    <div class="mc-right"><span class="mc-diff hard">Hard</span><a href="#holo" class="mc-btn">Notes ↓</a></div>
  </div>

  <div class="machine-card" data-os="redteam" data-diff="hard">
    <div class="mc-left"><span class="mc-os redteam">🔴</span><div><h4 class="mc-name">Throwback Network</h4><span class="mc-ip">Network Lab</span></div></div>
    <div class="mc-mid"><span class="mc-tech">Multi-host corporate simulation · phishing → internal pivot → exfil</span></div>
    <div class="mc-right"><span class="mc-diff hard">Hard</span><a href="#throwback" class="mc-btn">Notes ↓</a></div>
  </div>

</div>

---

## 🌐 Web Hacking Rooms

<div class="machines-list">

  <div class="machine-card" data-os="web" data-diff="easy">
    <div class="mc-left"><span class="mc-os web">🌐</span><div><h4 class="mc-name">OWASP Top 10 (2021)</h4><span class="mc-ip">Free</span></div></div>
    <div class="mc-mid"><span class="mc-tech">All 10 categories with hands-on labs — Broken Access, SSRF, SSTI, etc.</span></div>
    <div class="mc-right"><span class="mc-diff easy">Easy</span><a href="#owasp10" class="mc-btn">Notes ↓</a></div>
  </div>

  <div class="machine-card" data-os="web" data-diff="medium">
    <div class="mc-left"><span class="mc-os web">🌐</span><div><h4 class="mc-name">SQL Injection Lab</h4><span class="mc-ip">Standalone</span></div></div>
    <div class="mc-mid"><span class="mc-tech">Union-based · blind boolean · time-based · SQLMap usage</span></div>
    <div class="mc-right"><span class="mc-diff medium">Medium</span><a href="#sqli-lab" class="mc-btn">Notes ↓</a></div>
  </div>

  <div class="machine-card" data-os="web" data-diff="medium">
    <div class="mc-left"><span class="mc-os web">🌐</span><div><h4 class="mc-name">Advent of Cyber (Web)</h4><span class="mc-ip">Annual</span></div></div>
    <div class="mc-mid"><span class="mc-tech">XSS · RCE via file upload · JWT manipulation · IDOR · SSRF</span></div>
    <div class="mc-right"><span class="mc-diff easy">Easy</span><a href="#aoc-web" class="mc-btn">Notes ↓</a></div>
  </div>

  <div class="machine-card" data-os="web" data-diff="hard">
    <div class="mc-left"><span class="mc-os web">🌐</span><div><h4 class="mc-name">Attacking ICS Plant</h4><span class="mc-ip">Industrial</span></div></div>
    <div class="mc-mid"><span class="mc-tech">SCADA web panel exploitation · Modbus protocol abuse · HMI takeover</span></div>
    <div class="mc-right"><span class="mc-diff hard">Hard</span><a href="#ics" class="mc-btn">Notes ↓</a></div>
  </div>

</div>

---

## 🏢 Active Directory Rooms

<div class="machines-list">

  <div class="machine-card" data-os="ad" data-diff="medium">
    <div class="mc-left"><span class="mc-os ad">🏢</span><div><h4 class="mc-name">Active Directory Basics</h4><span class="mc-ip">Free</span></div></div>
    <div class="mc-mid"><span class="mc-tech">LDAP structure · users/groups/GPOs · authentication flows · trusts</span></div>
    <div class="mc-right"><span class="mc-diff easy">Easy</span><a href="#ad-basics" class="mc-btn">Notes ↓</a></div>
  </div>

  <div class="machine-card" data-os="ad" data-diff="medium">
    <div class="mc-left"><span class="mc-os ad">🏢</span><div><h4 class="mc-name">Attacktive Directory</h4><span class="mc-ip">10.10.x.x</span></div></div>
    <div class="mc-mid"><span class="mc-tech">AS-REP Roasting → Kerberoasting → Secretsdump → pass-the-hash</span></div>
    <div class="mc-right"><span class="mc-diff medium">Medium</span><a href="#attacktive" class="mc-btn">Notes ↓</a></div>
  </div>

  <div class="machine-card" data-os="ad" data-diff="hard">
    <div class="mc-left"><span class="mc-os ad">🏢</span><div><h4 class="mc-name">Post-Exploitation Basics</h4><span class="mc-ip">Path</span></div></div>
    <div class="mc-mid"><span class="mc-tech">BloodHound · token impersonation · Golden/Silver tickets · persistence</span></div>
    <div class="mc-right"><span class="mc-diff hard">Hard</span><a href="#postexploit-ad" class="mc-btn">Notes ↓</a></div>
  </div>

</div>

---

## 🔬 Forensics & OSINT Rooms

<div class="machines-list">

  <div class="machine-card" data-os="forensics" data-diff="medium">
    <div class="mc-left"><span class="mc-os dfir">🔬</span><div><h4 class="mc-name">Volatility</h4><span class="mc-ip">Memory</span></div></div>
    <div class="mc-mid"><span class="mc-tech">Memory forensics with Volatility 3 — processes, network, credentials</span></div>
    <div class="mc-right"><span class="mc-diff medium">Medium</span><a href="#volatility" class="mc-btn">Notes ↓</a></div>
  </div>

  <div class="machine-card" data-os="forensics" data-diff="medium">
    <div class="mc-left"><span class="mc-os dfir">🔬</span><div><h4 class="mc-name">Autopsy</h4><span class="mc-ip">Disk</span></div></div>
    <div class="mc-mid"><span class="mc-tech">Disk image analysis · deleted file recovery · timeline analysis · artifact carving</span></div>
    <div class="mc-right"><span class="mc-diff medium">Medium</span><a href="#autopsy" class="mc-btn">Notes ↓</a></div>
  </div>

  <div class="machine-card" data-os="osint" data-diff="easy">
    <div class="mc-left"><span class="mc-os osint">🕵️</span><div><h4 class="mc-name">OhSINT</h4><span class="mc-ip">OSINT</span></div></div>
    <div class="mc-mid"><span class="mc-tech">Image EXIF metadata → GPS coords → social media → email → password</span></div>
    <div class="mc-right"><span class="mc-diff easy">Easy</span><a href="#ohsint" class="mc-btn">Notes ↓</a></div>
  </div>

  <div class="machine-card" data-os="osint" data-diff="medium">
    <div class="mc-left"><span class="mc-os osint">🕵️</span><div><h4 class="mc-name">Searchlight OSINT</h4><span class="mc-ip">OSINT</span></div></div>
    <div class="mc-mid"><span class="mc-tech">Advanced OSINT: domain footprinting · social graph analysis · geolocation</span></div>
    <div class="mc-right"><span class="mc-diff medium">Medium</span><a href="#searchlight" class="mc-btn">Notes ↓</a></div>
  </div>

</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
  const filterBtns = document.querySelectorAll('.mf-btn');
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
