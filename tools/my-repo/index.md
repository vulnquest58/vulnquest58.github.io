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

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md); border: 1px solid rgba(59,130,246,0.35); background: rgba(59,130,246,0.04);">
    <div class="card-icon" style="font-size: 2.2rem; margin-bottom: 0;">🛡️</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">UAC Apex Framework (AEF) v4.0</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Enterprise-grade adaptive UAC elevation framework for Windows. Context-aware technique selection, pre-flight risk scoring, retry/fallback orchestration, and full cleanup pipeline.
      </p>
      <div style="margin-top: 6px; display:flex; gap:6px; flex-wrap:wrap;">
        <span style="background:rgba(59,130,246,0.15);color:#93c5fd;border:1px solid rgba(59,130,246,0.35);padding:2px 8px;border-radius:4px;font-size:0.75rem;font-family:var(--font-mono);">C++17</span>
        <span style="background:rgba(124,58,237,0.12);color:#a78bfa;border:1px solid rgba(124,58,237,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;font-family:var(--font-mono);">Windows</span>
        <span style="background:rgba(15,160,70,0.12);color:#4ade80;border:1px solid rgba(15,160,70,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">v4.0.0</span>
        <span style="background:rgba(234,179,8,0.12);color:#fbbf24;border:1px solid rgba(234,179,8,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">CMake</span>
      </div>
    </div>
    <div style="display:flex; flex-direction:column; gap:6px; flex-shrink:0;">
      <a href="{{ '/tools/my-repo/uac-apex/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; text-decoration: none;">View Report →</a>
      <a href="https://github.com/vulnquest58/uac-apex-framework" target="_blank" class="btn btn-primary" style="padding: 6px 12px; font-size: 0.85rem; text-decoration: none; box-shadow:none;"><i class="fab fa-github"></i> GitHub</a>
    </div>
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

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md); border: 1px solid rgba(15,160,70,0.35); background: rgba(15,160,70,0.04);">
    <div class="card-icon" style="font-size: 2.2rem; margin-bottom: 0;">🎮</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">vuln_hmv</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Full-featured HackMyVM CLI — browse VMs, compare local library, resolve MEGA links, submit flags, and view the leaderboard. Includes <code>setup.sh</code> for system-wide install to <code>/usr/local/bin</code>.
      </p>
      <div style="margin-top: 6px; display:flex; gap:6px; flex-wrap:wrap;">
        <span style="background:rgba(59,130,246,0.15);color:#93c5fd;border:1px solid rgba(59,130,246,0.35);padding:2px 8px;border-radius:4px;font-size:0.75rem;font-family:var(--font-mono);">Python 3.8+</span>
        <span style="background:rgba(15,160,70,0.12);color:#4ade80;border:1px solid rgba(15,160,70,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">Linux · macOS</span>
        <span style="background:rgba(234,179,8,0.12);color:#fbbf24;border:1px solid rgba(234,179,8,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">HackMyVM</span>
      </div>
    </div>
    <div style="display:flex; flex-direction:column; gap:6px; flex-shrink:0;">
      <a href="{{ '/tools/my-repo/vuln-hmv/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; text-decoration: none;">View Guide →</a>
      <a href="https://github.com/vulnquest58/vuln_hmv" target="_blank" class="btn btn-primary" style="padding: 6px 12px; font-size: 0.85rem; text-decoration: none; box-shadow:none;"><i class="fab fa-github"></i> GitHub</a>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md); border: 1px solid rgba(59,130,246,0.35); background: rgba(59,130,246,0.04);">
    <div class="card-icon" style="font-size: 2.2rem; margin-bottom: 0;">📥</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">mega-download-cli</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Batch MEGA downloader with live progress bar, smart selection (<code>--select</code>, <code>--level</code>), HackMyVM direct download (<code>--hmv</code>), and auto-MEGA-CMD installer for Windows/Linux/macOS.
      </p>
      <div style="margin-top: 6px; display:flex; gap:6px; flex-wrap:wrap;">
        <span style="background:rgba(59,130,246,0.15);color:#93c5fd;border:1px solid rgba(59,130,246,0.35);padding:2px 8px;border-radius:4px;font-size:0.75rem;font-family:var(--font-mono);">Python 3.8+</span>
        <span style="background:rgba(15,160,70,0.12);color:#4ade80;border:1px solid rgba(15,160,70,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">Windows · Linux · macOS</span>
        <span style="background:rgba(124,58,237,0.12);color:#a78bfa;border:1px solid rgba(124,58,237,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">MEGA-CMD</span>
      </div>
    </div>
    <div style="display:flex; flex-direction:column; gap:6px; flex-shrink:0;">
      <a href="{{ '/tools/my-repo/mega-download-cli/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; text-decoration: none;">View Guide →</a>
      <a href="https://github.com/vulnquest58/mega-download-cli" target="_blank" class="btn btn-primary" style="padding: 6px 12px; font-size: 0.85rem; text-decoration: none; box-shadow:none;"><i class="fab fa-github"></i> GitHub</a>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md); border: 1px solid rgba(168,85,247,0.4); background: rgba(168,85,247,0.04);">
    <div class="card-icon" style="font-size: 2.2rem; margin-bottom: 0;">🐚</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">NexShell</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Elite reverse shell commander — cross-platform (Linux/Windows/macOS), 15+ payloads, AMSI bypass, AD Recon, Persistence, Container Escape. No dependencies.
      </p>
      <div style="margin-top: 6px; display:flex; gap:6px; flex-wrap:wrap;">
        <span style="background:rgba(168,85,247,0.15);color:#a78bfa;border:1px solid rgba(168,85,247,0.35);padding:2px 8px;border-radius:4px;font-size:0.75rem;font-family:var(--font-mono);">Python 3.6+</span>
        <span style="background:rgba(15,160,70,0.12);color:#4ade80;border:1px solid rgba(15,160,70,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">Linux · Windows · macOS</span>
        <span style="background:rgba(6,182,212,0.12);color:#22d3ee;border:1px solid rgba(6,182,212,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">No Dependencies</span>
        <span style="background:rgba(239,68,68,0.12);color:#f87171;border:1px solid rgba(239,68,68,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">Red Team</span>
      </div>
    </div>
    <div style="display:flex; flex-direction:column; gap:6px; flex-shrink:0;">
      <a href="{{ '/tools/my-repo/nexshell/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; text-decoration: none;">View Guide →</a>
      <a href="https://github.com/vulnquest58/nexshell" target="_blank" class="btn btn-primary" style="padding: 6px 12px; font-size: 0.85rem; text-decoration: none; box-shadow:none;"><i class="fab fa-github"></i> GitHub</a>
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
