---
layout: page
title: "Specialty Guide: Reconnaissance Tools"
subtitle: "Tools for passive and active asset discovery"
permalink: /bugbounty/tools/recon/
---

## 🔍 Attack Surface Discovery Tools

Reconnaissance is focused on finding hidden assets, IP spaces, and domains owned by the target organization. Select an active tool from the index below to view detailed setups, mechanics, and cheatsheet commands.

<div class="cards-grid">

  <div class="card">
    <div class="card-icon">🧭</div>
    <h3 class="card-title">Subfinder</h3>
    <p class="card-description">
      Fast passive subdomain discovery engine that queries APIs to gather historical subdomain lists without active traffic.
    </p>
    <a href="{{ '/bugbounty/tools/recon/subfinder/' | relative_url }}" class="card-link">View Wiki & Cheatsheet →</a>
  </div>

  <div class="card">
    <div class="card-icon">🌐</div>
    <h3 class="card-title">OWASP Amass</h3>
    <p class="card-description">
      In-depth asset mapping, active and passive subdomain collection, ASN correlation, and active DNS resolution.
    </p>
    <a href="{{ '/bugbounty/tools/recon/amass/' | relative_url }}" class="card-link">View Wiki & Cheatsheet →</a>
  </div>

  <div class="card">
    <div class="card-icon">🎯</div>
    <h3 class="card-title">Naabu</h3>
    <p class="card-description">
      High-speed TCP/UDP port scanner leveraging raw sockets to quickly identify open service ports.
    </p>
    <a href="{{ '/bugbounty/tools/recon/naabu/' | relative_url }}" class="card-link">View Wiki & Cheatsheet →</a>
  </div>

</div>

---

### 🔗 Back to Toolkit
- [Return to Main Tools Listing]({{ '/bugbounty/tools/' | relative_url }})
