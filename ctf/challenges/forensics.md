---
layout: page
title: Digital Forensics
subtitle: CTF forensics challenge writeups by event and year
permalink: /ctf/challenges/forensics/
---

<p class="page-lead">Digital forensics and incident response (DFIR) writeups from Google CTF, DEF CON, picoCTF, and other global competitions. Organized by year and event.</p>

<div class="challenge-year-nav">
  <button class="mf-btn active" data-filter="all">All Years</button>
  <button class="mf-btn" data-filter="2025">2025</button>
  <button class="mf-btn" data-filter="2024">2024</button>
</div>

---

## 2025 Challenges

### Google CTF 2025

<div class="challenge-cards-list">

  <div class="challenge-card" data-year="2025" data-event="google">
    <div class="cc-header">
      <div class="cc-title-area">
        <span class="cc-event-badge google">Google CTF 2025</span>
        <h4 class="cc-name">PacketMonster</h4>
      </div>
      <span class="cc-diff easy">Easy</span>
    </div>
    <div class="cc-body">
      <p><strong>Category</strong>: Forensics · <strong>Points</strong>: 100 · <strong>Solves</strong>: 580</p>
      <p class="cc-desc">A network PCAP file containing suspicious port scanning and TCP streams. Locate the payload transmission stream and carve out the hidden files.</p>
      <div class="cc-tags"><span>PCAP</span><span>Wireshark</span><span>TCP Stream</span><span>File Carving</span></div>
    </div>
    <div class="cc-solution">
      <details>
        <summary>View Approach</summary>
        <div class="cc-solution-body">
          <p>1. Open the PCAP file in Wireshark. Filter by <code>http</code> or <code>tcp.port == 80</code> to isolate web traffic.</p>
          <p>2. Locate a large POST request transferring binary data: stream index 14.</p>
          <p>3. Right-click, select "Follow TCP Stream", view data as "Raw", and click "Save as..." to save it as <code>transfer.bin</code>.</p>
          <p>4. Run <code>binwalk -e transfer.bin</code> to unpack the zipped file containing the flag.</p>
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
        <h4 class="cc-name">MemDissect</h4>
      </div>
      <span class="cc-diff medium">Medium</span>
    </div>
    <div class="cc-body">
      <p><strong>Category</strong>: Forensics · <strong>Points</strong>: 260 · <strong>Solves</strong>: 140</p>
      <p class="cc-desc">Memory dump of a Windows Server compromised via LSASS dumping. Use Volatility 3 to locate the LSASS process and recover NT hashes.</p>
      <div class="cc-tags"><span>Volatility 3</span><span>Memory Forensics</span><span>LSASS</span><span>Credential Dumping</span></div>
    </div>
    <div class="cc-solution">
      <details>
        <summary>View Approach</summary>
        <div class="cc-solution-body">
          <p>1. Run Volatility info plugin to identify the OS: <code>python3 vol.py -f mem.raw windows.info</code>.</p>
          <p>2. List active processes to confirm lsass.exe was dumped: <code>windows.pslist</code>.</p>
          <p>3. Dump credentials using the hashdump plugin: <code>python3 vol.py -f mem.raw windows.hashdump.Hashdump</code>.</p>
          <p>4. Crack the administrator hash using John or Hashcat to find the secret passphrase flag.</p>
        </div>
      </details>
    </div>
  </div>

</div>
---
