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