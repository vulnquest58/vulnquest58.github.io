---
layout: page
title: C2 Frameworks
subtitle: Command & Control infrastructure setup and management
permalink: /redteam/c2-frameworks/
---

## Command & Control Infrastructure

Command and Control (C2) frameworks are the backbone of modern red team operations. I configure, customize, and maintain multiple C2 systems to adapt to diverse environments and security controls.

<div class="c2-grid">

  <div class="c2-card">
    <div class="c2-title-section">
      <h3>Sliver C2</h3>
      <span class="badge badge-success">Active / Primary</span>
    </div>
    <p>Go-based multi-user C2 framework. Primary choice for high-evasion implants (supporting beacon and session modes) over DNS, HTTPS, and WireGuard.</p>
    <a href="{{ '/redteam/c2-frameworks/sliver/' | relative_url }}" class="btn btn-secondary">Configuration Details</a>
  </div>

  <div class="c2-card">
    <div class="c2-title-section">
      <h3>Havoc C2</h3>
      <span class="badge badge-info">Active / Secondary</span>
    </div>
    <p>Modern C++ framework with dynamic payload generation (Demon). Specialized in bypassing API hooking and memory scanning using sleep obfuscation.</p>
    <a href="{{ '/redteam/c2-frameworks/havoc/' | relative_url }}" class="btn btn-secondary">Configuration Details</a>
  </div>

  <div class="c2-card">
    <div class="c2-title-section">
      <h3>Empire C2</h3>
      <span class="badge badge-dark">Legacy / Testing</span>
    </div>
    <p>Python and PowerShell-focused post-exploitation framework. Excellent for internal Windows AD post-exploitation and scripting integration.</p>
    <a href="{{ '/redteam/c2-frameworks/empire/' | relative_url }}" class="btn btn-secondary">Configuration Details</a>
  </div>

  <div class="c2-card">
    <div class="c2-title-section">
      <h3>Covenant C2</h3>
      <span class="badge badge-dark">Legacy / Testing</span>
    </div>
    <p>.NET-based C2 framework. Designed for advanced C# compilation, dynamic tasking, and executing assembly code directly in memory.</p>
    <a href="{{ '/redteam/c2-frameworks/covenant/' | relative_url }}" class="btn btn-secondary">Configuration Details</a>
  </div>

  <div class="c2-card">
    <div class="c2-title-section">
      <h3>Mythic C2</h3>
      <span class="badge badge-info">Active / Testing</span>
    </div>
    <p>Collaborative, containerized multi-platform C2 portal. Highly modular architecture allowing third-party agents and custom transport profiles.</p>
    <a href="{{ '/redteam/c2-frameworks/mythic/' | relative_url }}" class="btn btn-secondary">Configuration Details</a>
  </div>

</div>
