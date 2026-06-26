---
layout: page
title: "Specialty Guide: Active Directory & Internal Pentest"
subtitle: "Tools for AD path visualization, SMB relays, and Kerberos attacks"
permalink: /tools/active-directory/
---

## 🛡️ Active Directory & Internal Pentest (فحص خوادم الشبكة الداخلية)

This category focuses on Active Directory domain enumeration, lateral movement, Kerberos authentication attacks, and internal protocol poisoning.

### Tool Catalog

<div class="vertical-cards-grid" style="display: flex; flex-direction: column; gap: var(--spacing-md); max-width: 800px; margin: var(--spacing-xl) 0;">

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🌐</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">BloodHound & SharpHound</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Active Directory relationship mapping engine using graph databases to trace permission vectors.
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">⚙️</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Impacket Suite</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        A collection of Python classes for working with network protocols (SMB, Kerberos, LDAP, WMI).
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🛡️</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">CrackMapExec</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        A swiss-army knife for pentesting networks, designed to automate post-exploitation tasks on large Active Directory environments.
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🔑</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Kerbrute / Rubeus</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Utilities to brute-force usernames/passwords via Kerberos and perform ticket operations (AS-REP Roasting, Kerberoasting).
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">📡</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Responder / ntlmrelayx</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Protocol poisoning (LLMNR/NBT-NS) and relay tools to intercept and replay Windows hash credentials.
      </p>
    </div>
  </div>

</div>

---

### 🔗 Back to Toolkit
- [Return to Main Tools Listing]({{ '/tools/' | relative_url }})
