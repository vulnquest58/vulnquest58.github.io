---
layout: page
title: "Custom Repository: myrepo"
subtitle: "In-house offensive tooling and automation scripts"
permalink: /tools/my-repo/
---

## 🛠️ In-House Development & Automations

A catalog of custom-built offensive security tools and utility setups. Select any card below to view detailed specifications, design blueprints, and execution guides.

<div class="vertical-cards-grid" style="display: flex; flex-direction: column; gap: var(--spacing-md); max-width: 800px; margin: var(--spacing-xl) 0;">

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2.2rem; margin-bottom: 0;">🔎</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">VULNTRACE</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Dynamic vulnerability tracer that hooks Winsock/POSIX APIs, tracing memory taint allocation in real-time.
      </p>
    </div>
    <a href="{{ '/tools/vulntrace/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none;">View Wiki →</a>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2.2rem; margin-bottom: 0;">💻</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Kali Master</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Automated provisioning shell configuration to instantly build and customize Kali Linux deployments.
      </p>
    </div>
    <a href="{{ '/tools/kali-master/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none;">View Wiki →</a>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2.2rem; margin-bottom: 0;">📦</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Lab Manager</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Vulnerable laboratory network orchestration using Vagrant/Docker container provisioning templates.
      </p>
    </div>
    <a href="{{ '/tools/lab-manager/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none;">View Wiki →</a>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2.2rem; margin-bottom: 0;">📜</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Custom Scripts</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Active Directory enumerators, custom payload builders, and automated recon piping scripts.
      </p>
    </div>
    <a href="{{ '/tools/custom-scripts/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none;">View Wiki →</a>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md); border: 1px solid rgba(220,38,38,0.35); background: rgba(220,38,38,0.05);">
    <div class="card-icon" style="font-size: 2.2rem; margin-bottom: 0;">💀</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">DirtyClone Exploit Framework</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Professional exploit framework for CVE-2026-46331 — Linux kernel LPE via TC pedit + IPsec page-cache corruption. 8-stage automated attack chain in C + Python.
      </p>
      <div style="margin-top: 6px; display:flex; gap:6px; flex-wrap:wrap;">
        <span style="background:rgba(220,38,38,0.2);color:#f87171;border:1px solid rgba(220,38,38,0.4);padding:2px 8px;border-radius:4px;font-size:0.75rem;font-family:var(--font-mono);">CVE-2026-46331</span>
        <span style="background:rgba(124,58,237,0.15);color:#a78bfa;border:1px solid rgba(124,58,237,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;font-family:var(--font-mono);">C / Python</span>
        <span style="background:rgba(15,160,70,0.15);color:#4ade80;border:1px solid rgba(15,160,70,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">v1.0.0</span>
      </div>
    </div>
    <div style="display:flex; flex-direction:column; gap:6px; flex-shrink:0;">
      <a href="{{ '/tools/my-repo/dirtyclone/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; text-decoration: none;">View Report →</a>
      <a href="https://github.com/vulnquest58/dirtyclone-exploit" target="_blank" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; text-decoration: none;"><i class="fab fa-github"></i> GitHub</a>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md); border: 2px dashed var(--border-color);">
    <div class="card-icon" style="font-size: 2.2rem; margin-bottom: 0;"><i class="fab fa-github"></i></div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">myrepo on GitHub</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Direct access to all open-source repositories, release packages, and custom scripts on my profile.
      </p>
    </div>
    <a href="https://github.com/vulnquest58" target="_blank" class="btn btn-primary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none; box-shadow: none;">GitHub Profile →</a>
  </div>

</div>

---

### 🔗 Back to Toolkit
- [Return to Main Tools Listing]({{ '/tools/' | relative_url }})
