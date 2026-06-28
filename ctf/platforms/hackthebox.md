---
layout: page
title: Hack The Box
subtitle: Machine writeups organized by OS, difficulty, and technique
permalink: /ctf/platforms/hackthebox/
platform: HackTheBox
---

<div class="platform-hero htb-hero">
  <div class="plat-hero-icon">⬡</div>
  <div class="plat-hero-text">
    <h2>Hack The Box</h2>
    <p>Standalone machines, Active Directory ProLabs, Sherlocks (DFIR), and competitive challenges.</p>
    <div class="plat-hero-badges">
      <span class="badge badge-success">Rank: Pro Hacker</span>
      <span class="badge badge-info">40+ Machines Owned</span>
      <span class="badge badge-warning">25+ Challenges</span>
    </div>
  </div>
</div>

<div class="machine-filter-bar">
  <button class="mf-btn active" data-filter="all">All</button>
  <button class="mf-btn" data-filter="linux">🐧 Linux</button>
  <button class="mf-btn" data-filter="windows">🪟 Windows</button>
  <button class="mf-btn" data-filter="active-directory">🏢 Active Directory</button>
  <button class="mf-btn" data-filter="easy">Easy</button>
  <button class="mf-btn" data-filter="medium">Medium</button>
  <button class="mf-btn" data-filter="hard">Hard</button>
  <button class="mf-btn" data-filter="insane">Insane</button>
</div>

---

## 🐧 Linux Machines

<div class="machines-list">

  <div class="machine-card" data-os="linux" data-diff="easy">
    <div class="mc-left">
      <span class="mc-os linux">🐧</span>
      <div>
        <h4 class="mc-name">WingData</h4>
        <span class="mc-ip">10.129.244.106</span>
      </div>
    </div>
    <div class="mc-mid">
      <span class="mc-tech">CVE-2025-47812 Wing FTP Null-Byte Lua RCE · SHA256 Hash Cracking · CVE-2025-4517 Python tarfile Arbitrary Write</span>
    </div>
    <div class="mc-right">
      <span class="mc-diff easy">Easy</span>
      <a href="{{ '/ctf/platforms/hackthebox/wingdata/' | relative_url }}" class="mc-btn">Writeup →</a>
    </div>
  </div>

  <div class="machine-card" data-os="linux" data-diff="easy">
    <div class="mc-left">
      <span class="mc-os linux">🐧</span>
      <div>
        <h4 class="mc-name">OpenAdmin</h4>
        <span class="mc-ip">10.10.10.171</span>
      </div>
    </div>
    <div class="mc-mid">
      <span class="mc-tech">OpenNetAdmin RCE · SSH key LFI · sudo nano GTFOBin</span>
    </div>
    <div class="mc-right">
      <span class="mc-diff easy">Easy</span>
      <a href="{{ '/ctf/writeups/hackthebox/openadmin/' | relative_url }}" class="mc-btn">Writeup →</a>
    </div>
  </div>

  <div class="machine-card" data-os="linux" data-diff="easy">
    <div class="mc-left">
      <span class="mc-os linux">🐧</span>
      <div>
        <h4 class="mc-name">Knife</h4>
        <span class="mc-ip">10.10.10.242</span>
      </div>
    </div>
    <div class="mc-mid">
      <span class="mc-tech">PHP 8.1 backdoor (CVE-2021-3129) · sudo knife GTFOBin</span>
    </div>
    <div class="mc-right">
      <span class="mc-diff easy">Easy</span>
      <a href="{{ '/ctf/writeups/hackthebox/knife/' | relative_url }}" class="mc-btn">Writeup →</a>
    </div>
  </div>

  <div class="machine-card" data-os="linux" data-diff="easy">
    <div class="mc-left">
      <span class="mc-os linux">🐧</span>
      <div>
        <h4 class="mc-name">Nibbles</h4>
        <span class="mc-ip">10.10.10.75</span>
      </div>
    </div>
    <div class="mc-mid">
      <span class="mc-tech">NibbleBlog file upload RCE · sudo script wildcard injection</span>
    </div>
    <div class="mc-right">
      <span class="mc-diff easy">Easy</span>
      <a href="{{ '/ctf/writeups/hackthebox/nibbles/' | relative_url }}" class="mc-btn">Writeup →</a>
    </div>
  </div>

  <div class="machine-card" data-os="linux" data-diff="medium">
    <div class="mc-left">
      <span class="mc-os linux">🐧</span>
      <div>
        <h4 class="mc-name">BountyHunter</h4>
        <span class="mc-ip">10.10.11.100</span>
      </div>
    </div>
    <div class="mc-mid">
      <span class="mc-tech">XXE → LFI · credential reuse · Python eval() code injection</span>
    </div>
    <div class="mc-right">
      <span class="mc-diff medium">Medium</span>
      <a href="{{ '/ctf/writeups/hackthebox/bountyhunter/' | relative_url }}" class="mc-btn">Writeup →</a>
    </div>
  </div>

  <div class="machine-card" data-os="linux" data-diff="medium">
    <div class="mc-left">
      <span class="mc-os linux">🐧</span>
      <div>
        <h4 class="mc-name">Horizontall</h4>
        <span class="mc-ip">10.10.11.105</span>
      </div>
    </div>
    <div class="mc-mid">
      <span class="mc-tech">Strapi CMS RCE (CVE-2019-19609) · Laravel telescopy SSRF → privesc</span>
    </div>
    <div class="mc-right">
      <span class="mc-diff medium">Medium</span>
      <a href="{{ '/ctf/writeups/hackthebox/horizontall/' | relative_url }}" class="mc-btn">Writeup →</a>
    </div>
  </div>

  <div class="machine-card" data-os="linux" data-diff="medium">
    <div class="mc-left">
      <span class="mc-os linux">🐧</span>
      <div>
        <h4 class="mc-name">Writer</h4>
        <span class="mc-ip">10.10.11.101</span>
      </div>
    </div>
    <div class="mc-mid">
      <span class="mc-tech">SQLi union-based · SSRF via file upload · APT hooks for root</span>
    </div>
    <div class="mc-right">
      <span class="mc-diff medium">Medium</span>
      <a href="{{ '/ctf/writeups/hackthebox/writer/' | relative_url }}" class="mc-btn">Writeup →</a>
    </div>
  </div>

  <div class="machine-card" data-os="linux" data-diff="hard">
    <div class="mc-left">
      <span class="mc-os linux">🐧</span>
      <div>
        <h4 class="mc-name">Scrambled</h4>
        <span class="mc-ip">10.10.11.168</span>
      </div>
    </div>
    <div class="mc-mid">
      <span class="mc-tech">Kerberos-only auth · Silver ticket attack · .NET deserialization RCE</span>
    </div>
    <div class="mc-right">
      <span class="mc-diff hard">Hard</span>
      <a href="{{ '/ctf/writeups/hackthebox/scrambled/' | relative_url }}" class="mc-btn">Writeup →</a>
    </div>
  </div>

</div>

---

## 🪟 Windows Machines

<div class="machines-list">

  <div class="machine-card" data-os="windows" data-diff="easy">
    <div class="mc-left">
      <span class="mc-os windows">🪟</span>
      <div>
        <h4 class="mc-name">Blue</h4>
        <span class="mc-ip">10.10.10.40</span>
      </div>
    </div>
    <div class="mc-mid">
      <span class="mc-tech">EternalBlue (MS17-010) · SMBv1 exploitation · SYSTEM shell</span>
    </div>
    <div class="mc-right">
      <span class="mc-diff easy">Easy</span>
      <a href="{{ '/ctf/writeups/hackthebox/blue/' | relative_url }}" class="mc-btn">Writeup →</a>
    </div>
  </div>

  <div class="machine-card" data-os="windows" data-diff="easy">
    <div class="mc-left">
      <span class="mc-os windows">🪟</span>
      <div>
        <h4 class="mc-name">Legacy</h4>
        <span class="mc-ip">10.10.10.4</span>
      </div>
    </div>
    <div class="mc-mid">
      <span class="mc-tech">MS08-067 · SMB NetAPI buffer overflow · no auth required</span>
    </div>
    <div class="mc-right">
      <span class="mc-diff easy">Easy</span>
      <a href="{{ '/ctf/writeups/hackthebox/legacy/' | relative_url }}" class="mc-btn">Writeup →</a>
    </div>
  </div>

  <div class="machine-card" data-os="windows" data-diff="medium">
    <div class="mc-left">
      <span class="mc-os windows">🪟</span>
      <div>
        <h4 class="mc-name">Resolute</h4>
        <span class="mc-ip">10.10.10.169</span>
      </div>
    </div>
    <div class="mc-mid">
      <span class="mc-tech">RPC null session user enum · password spray · DNSAdmins DLL injection</span>
    </div>
    <div class="mc-right">
      <span class="mc-diff medium">Medium</span>
      <a href="{{ '/ctf/writeups/hackthebox/resolute/' | relative_url }}" class="mc-btn">Writeup →</a>
    </div>
  </div>

  <div class="machine-card" data-os="windows" data-diff="medium">
    <div class="mc-left">
      <span class="mc-os windows">🪟</span>
      <div>
        <h4 class="mc-name">Sauna</h4>
        <span class="mc-ip">10.10.10.175</span>
      </div>
    </div>
    <div class="mc-mid">
      <span class="mc-tech">AS-REP Roasting · AutoLogon creds · DCSync via GetChangesAll</span>
    </div>
    <div class="mc-right">
      <span class="mc-diff medium">Medium</span>
      <a href="{{ '/ctf/writeups/hackthebox/sauna/' | relative_url }}" class="mc-btn">Writeup →</a>
    </div>
  </div>

  <div class="machine-card" data-os="windows" data-diff="hard">
    <div class="mc-left">
      <span class="mc-os windows">🪟</span>
      <div>
        <h4 class="mc-name">Mantis</h4>
        <span class="mc-ip">10.10.10.52</span>
      </div>
    </div>
    <div class="mc-mid">
      <span class="mc-tech">OrchardCMS MSSQL creds · MS14-068 Kerberos PAC forgery</span>
    </div>
    <div class="mc-right">
      <span class="mc-diff hard">Hard</span>
      <a href="{{ '/ctf/writeups/hackthebox/mantis/' | relative_url }}" class="mc-btn">Writeup →</a>
    </div>
  </div>

  <div class="machine-card" data-os="windows" data-diff="hard">
    <div class="mc-left">
      <span class="mc-os windows">🪟</span>
      <div>
        <h4 class="mc-name">NanoCorp</h4>
        <span class="mc-ip">10.129.243.199</span>
      </div>
    </div>
    <div class="mc-mid">
      <span class="mc-tech">CVE-2025-24071 .library-ms NTLM Leak · BloodHound ACL Abuse · Protected Users Kerberos · CVE-2024-0670 Checkmk LPE</span>
    </div>
    <div class="mc-right">
      <span class="mc-diff hard">Hard</span>
      <a href="{{ '/ctf/platforms/hackthebox/nanocorp/' | relative_url }}" class="mc-btn">Writeup →</a>
    </div>
  </div>

</div>

---


## 🏢 Active Directory Machines

<div class="machines-list">

  <div class="machine-card" data-os="active-directory" data-diff="hard">
    <div class="mc-left">
      <span class="mc-os ad">🏢</span>
      <div>
        <h4 class="mc-name">Forest</h4>
        <span class="mc-ip">10.10.10.161</span>
      </div>
    </div>
    <div class="mc-mid">
      <span class="mc-tech">AS-REP Roast → BloodHound → WriteDACL → DCSync</span>
    </div>
    <div class="mc-right">
      <span class="mc-diff hard">Hard</span>
      <a href="{{ '/ctf/writeups/hackthebox/forest/' | relative_url }}" class="mc-btn">Writeup →</a>
    </div>
  </div>

  <div class="machine-card" data-os="active-directory" data-diff="hard">
    <div class="mc-left">
      <span class="mc-os ad">🏢</span>
      <div>
        <h4 class="mc-name">Active</h4>
        <span class="mc-ip">10.10.10.100</span>
      </div>
    </div>
    <div class="mc-mid">
      <span class="mc-tech">GPP password decryption (cpasswd) → Kerberoasting Administrator</span>
    </div>
    <div class="mc-right">
      <span class="mc-diff hard">Hard</span>
      <a href="{{ '/ctf/writeups/hackthebox/active/' | relative_url }}" class="mc-btn">Writeup →</a>
    </div>
  </div>

  <div class="machine-card" data-os="active-directory" data-diff="insane">
    <div class="mc-left">
      <span class="mc-os ad">🏢</span>
      <div>
        <h4 class="mc-name">Offshore ProLab</h4>
        <span class="mc-ip">ProLab</span>
      </div>
    </div>
    <div class="mc-mid">
      <span class="mc-tech">Multi-domain AD forest · ADCS ESC1 · Kerberos delegation chains</span>
    </div>
    <div class="mc-right">
      <span class="mc-diff insane">ProLab</span>
      <a href="{{ '/ctf/writeups/hackthebox/offshore/' | relative_url }}" class="mc-btn">Writeup →</a>
    </div>
  </div>

</div>

---

## 🔬 Sherlocks (DFIR)

<div class="machines-list">

  <div class="machine-card" data-os="dfir" data-diff="easy">
    <div class="mc-left">
      <span class="mc-os dfir">🔬</span>
      <div>
        <h4 class="mc-name">Brutus</h4>
        <span class="mc-ip">auth.log · wtmp</span>
      </div>
    </div>
    <div class="mc-mid">
      <span class="mc-tech">SSH brute-force analysis · backdoor user detection from auth.log</span>
    </div>
    <div class="mc-right">
      <span class="mc-diff easy">Easy</span>
      <a href="{{ '/ctf/writeups/hackthebox/brutus/' | relative_url }}" class="mc-btn">Writeup →</a>
    </div>
  </div>

  <div class="machine-card" data-os="dfir" data-diff="medium">
    <div class="mc-left">
      <span class="mc-os dfir">🔬</span>
      <div>
        <h4 class="mc-name">Noted</h4>
        <span class="mc-ip">Memory dump</span>
      </div>
    </div>
    <div class="mc-mid">
      <span class="mc-tech">Volatility memory analysis · credential extraction · process timeline</span>
    </div>
    <div class="mc-right">
      <span class="mc-diff medium">Medium</span>
      <a href="{{ '/ctf/writeups/hackthebox/noted/' | relative_url }}" class="mc-btn">Writeup →</a>
    </div>
  </div>

</div>

---


<script>
// Machine filter functionality
document.addEventListener('DOMContentLoaded', function() {
  const filterBtns = document.querySelectorAll('.mf-btn');
  const machineCards = document.querySelectorAll('.machine-card');

  filterBtns.forEach(btn => {
    btn.addEventListener('click', function() {
      const filter = this.dataset.filter;
      filterBtns.forEach(b => b.classList.remove('active'));
      this.classList.add('active');

      machineCards.forEach(card => {
        if (filter === 'all') {
          card.style.display = 'flex';
        } else if (card.dataset.os === filter || card.dataset.diff === filter) {
          card.style.display = 'flex';
        } else {
          card.style.display = 'none';
        }
      });
    });
  });
});
</script>
