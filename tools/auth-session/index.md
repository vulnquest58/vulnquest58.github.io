---
layout: page
title: "Specialty Guide: Authentication & Session Testing"
subtitle: "Tools for brute-forcing accounts and auditing session tokens"
permalink: /tools/auth-session/
---

## 🔐 Authentication & Session Testing

This category focuses on tools designed to brute-force web login protocols, dissect and forge JSON Web Tokens (JWT), and map out OAuth authorization flaws.

### Tool Catalog

<div class="vertical-cards-grid" style="display: flex; flex-direction: column; gap: var(--spacing-md); max-width: 800px; margin: var(--spacing-xl) 0;">

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🐉</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Hydra</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        A very fast network logon cracker supporting multiple authentication protocols (HTTP, SSH, FTP, Telnet).
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🏛️</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Medusa</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Speedy, parallel login brute forcer engine supporting modular protocols.
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🔑</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">jwt_tool</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Toolkit for auditing and exploiting JSON Web Tokens (including signature validation bypasses, None algorithm forgery, and key confusion).
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">💎</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Burp Suite Intruder / Authz</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Automated request replay plugins designed to test authentication rate-limiting and authorization boundary violations.
      </p>
    </div>
  </div>

</div>

---

### 🔗 Back to Toolkit
- [Return to Main Tools Listing]({{ '/tools/' | relative_url }})
