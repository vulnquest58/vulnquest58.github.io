---
layout: page
title: Red Teaming
subtitle: Advanced Adversary Simulation & Tradecraft
description: "Adversary simulation operations, custom Command and Control (C2) frameworks, EDR evasion, and Active Directory exploitation."
---

## Overview

Red teaming goes beyond traditional penetration testing to measure an organization's detection and response capabilities. This section documents my methodologies, custom tools, and operational logs for realistic adversary simulations.

## Core Capabilities

<div class="cards-grid">
  <div class="card">
    <div class="card-icon"><i class="fas fa-network-wired"></i></div>
    <h3 class="card-title">C2 Frameworks</h3>
    <p class="card-description">
      Developing and customizing Command & Control (C2) agents, profile configurations (Malleable C2), and redirectors.
    </p>
    <a href="/redteam/c2-frameworks/" class="card-link">Explore C2</a>
  </div>

  <div class="card">
    <div class="card-icon"><i class="fas fa-shield-alt"></i></div>
    <h3 class="card-title">Evasion & Tradecraft</h3>
    <p class="card-description">
      Researching AV/EDR evasion, API unhooking, custom loaders, and obfuscation techniques to maintain access.
    </p>
    <a href="/redteam/tradecraft/" class="card-link">Explore Tradecraft</a>
  </div>

  <div class="card">
    <div class="card-icon"><i class="fas fa-user-secret"></i></div>
    <h3 class="card-title">Operations</h3>
    <p class="card-description">
      Anonymized operational logs and post-exploitation timelines covering complex corporate networks.
    </p>
    <a href="/redteam/operations/" class="card-link">Explore Operations</a>
  </div>
</div>

## Operational Methodology

### 1. External Reconnaissance & Initial Access
- OSINT (LinkedIn, GitHub, DNS, SPF/DKIM/DMARC)
- Custom Phishing campaigns with HTML smushing
- Exploitation of public-facing edge services

### 2. Evasion & Payload Delivery
- Shellcode compilation using custom Nim/Rust loaders
- Direct syscalls and API unhooking to bypass modern EDRs
- Code signing with self-signed / leaked certificates

### 3. Lateral Movement & Active Directory
- Kerberoasting, AS-REP Roasting, and BloodHound analysis
- Overpass-the-Hash and Pass-the-Ticket attacks
- Exploitation of AD CS (Active Directory Certificate Services)

### 4. Persistence & Exfiltration
- WMI Event Subscriptions and scheduled tasks
- DLL hijacking in legitimate system binaries
- Covert DNS and HTTPS channels for data exfiltration

---

## Custom Offensive Tools

<div style="display:flex; flex-direction:column; gap:1rem; margin-top:0.5rem;">

  <div class="card" style="display:flex; align-items:center; gap:var(--spacing-md); padding:var(--spacing-md); border:1px solid rgba(59,130,246,0.35); background:rgba(59,130,246,0.04);">
    <div class="card-icon" style="font-size:2rem; margin-bottom:0;">🛡️</div>
    <div style="flex-grow:1;">
      <h3 class="card-title" style="margin-bottom:2px;">UAC Apex Framework (AEF) v4.0</h3>
      <p class="card-description" style="margin-bottom:4px; font-size:0.9rem;">
        Enterprise-grade adaptive UAC elevation framework for Windows — context-aware technique scoring, pre-flight risk assessment, retry/fallback orchestration, EDR/sandbox detection, and full cleanup pipeline.
      </p>
      <div style="display:flex; gap:6px; flex-wrap:wrap;">
        <span style="background:rgba(59,130,246,0.12);color:#93c5fd;border:1px solid rgba(59,130,246,0.3);padding:1px 7px;border-radius:4px;font-size:0.75rem;font-family:var(--font-mono);">C++17</span>
        <span style="background:rgba(234,179,8,0.12);color:#fbbf24;border:1px solid rgba(234,179,8,0.3);padding:1px 7px;border-radius:4px;font-size:0.75rem;">Windows</span>
        <span style="background:rgba(220,38,38,0.12);color:#f87171;border:1px solid rgba(220,38,38,0.3);padding:1px 7px;border-radius:4px;font-size:0.75rem;">UAC Bypass</span>
        <span style="background:rgba(15,160,70,0.12);color:#4ade80;border:1px solid rgba(15,160,70,0.3);padding:1px 7px;border-radius:4px;font-size:0.75rem;">v4.0.0</span>
      </div>
    </div>
    <div style="display:flex; flex-direction:column; gap:6px; flex-shrink:0;">
      <a href="{{ '/tools/my-repo/uac-apex/' | relative_url }}" class="btn btn-secondary" style="padding:6px 12px; font-size:0.85rem; text-decoration:none;">View Report →</a>
      <a href="https://github.com/vulnquest58/uac-apex-framework" target="_blank" class="btn btn-primary" style="padding:6px 12px; font-size:0.85rem; text-decoration:none; box-shadow:none;"><i class="fab fa-github"></i> GitHub</a>
    </div>
  </div>

  <div class="card" style="display:flex; align-items:center; gap:var(--spacing-md); padding:var(--spacing-md); border:1px solid rgba(220,38,38,0.35); background:rgba(220,38,38,0.04);">
    <div class="card-icon" style="font-size:2rem; margin-bottom:0;">💀</div>
    <div style="flex-grow:1;">
      <h3 class="card-title" style="margin-bottom:2px;">DirtyClone Exploit Framework</h3>
      <p class="card-description" style="margin-bottom:4px; font-size:0.9rem;">
        CVE-2026-46331 — Linux kernel LPE via TC pedit + IPsec page-cache corruption. 8-stage automated attack chain with shellcode delivery, persistence, and cleanup modules.
      </p>
      <div style="display:flex; gap:6px; flex-wrap:wrap;">
        <span style="background:rgba(220,38,38,0.15);color:#f87171;border:1px solid rgba(220,38,38,0.35);padding:1px 7px;border-radius:4px;font-size:0.75rem;font-family:var(--font-mono);">CVE-2026-46331</span>
        <span style="background:rgba(124,58,237,0.12);color:#a78bfa;border:1px solid rgba(124,58,237,0.3);padding:1px 7px;border-radius:4px;font-size:0.75rem;">C / Python</span>
        <span style="background:rgba(220,38,38,0.12);color:#f87171;border:1px solid rgba(220,38,38,0.3);padding:1px 7px;border-radius:4px;font-size:0.75rem;">Linux LPE</span>
      </div>
    </div>
    <div style="display:flex; flex-direction:column; gap:6px; flex-shrink:0;">
      <a href="{{ '/tools/my-repo/dirtyclone/' | relative_url }}" class="btn btn-secondary" style="padding:6px 12px; font-size:0.85rem; text-decoration:none;">View Report →</a>
      <a href="https://github.com/vulnquest58/dirtyclone-exploit" target="_blank" class="btn btn-secondary" style="padding:6px 12px; font-size:0.85rem; text-decoration:none;"><i class="fab fa-github"></i> GitHub</a>
    </div>
  </div>

</div>