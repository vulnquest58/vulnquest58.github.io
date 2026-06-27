---
layout: default
title: Home
description: "VulnQuest - Offensive Security Portfolio specializing in Bug Bounty, Red Teaming, Tools Development, and CTF Challenges"
permalink: /
---

<style>
  /* --- Cyber HUD Styling --- */
  .cyber-hud-container {
    background: rgba(10, 19, 24, 0.65);
    border: 1px solid rgba(0, 255, 102, 0.15);
    border-radius: var(--border-radius-lg);
    backdrop-filter: blur(8px);
    box-shadow: 0 0 25px rgba(0, 255, 102, 0.05);
    padding: var(--spacing-xl);
    margin-bottom: var(--spacing-2xl);
    position: relative;
    overflow: hidden;
  }
  .cyber-hud-container::after {
    content: '';
    position: absolute;
    top: 0;
    right: 0;
    width: 150px;
    height: 150px;
    background: radial-gradient(circle, rgba(0, 255, 102, 0.08) 0%, transparent 70%);
    pointer-events: none;
  }
  .hud-telemetry {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: var(--spacing-md);
    margin-top: var(--spacing-lg);
    border-top: 1px solid rgba(0, 255, 102, 0.1);
    padding-top: var(--spacing-md);
    font-family: var(--font-mono);
    font-size: 0.8rem;
    color: var(--text-muted);
  }
  .hud-item span {
    color: var(--accent-primary);
    font-weight: bold;
  }

  /* --- Stats Dashboard Grid --- */
  .stats-dashboard {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: var(--spacing-lg);
    margin: var(--spacing-xl) 0;
  }
  .stat-card {
    background: rgba(15, 26, 31, 0.8);
    border: 1px solid var(--border-color);
    border-radius: var(--border-radius);
    padding: var(--spacing-lg);
    text-align: center;
    transition: var(--transition);
    position: relative;
  }
  .stat-card:hover {
    border-color: var(--accent-primary);
    box-shadow: 0 0 15px rgba(0, 255, 102, 0.1);
    transform: translateY(-3px);
  }
  .stat-val {
    font-family: var(--font-mono);
    font-size: 2.2rem;
    font-weight: 800;
    background: var(--gradient-primary);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: var(--spacing-xs);
  }
  .stat-lbl {
    font-size: 0.85rem;
    color: var(--text-secondary);
    text-transform: uppercase;
    letter-spacing: 0.05em;
  }

  /* --- Certifications Styling --- */
  .certs-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: var(--spacing-md);
    margin: var(--spacing-xl) 0;
  }
  .cert-badge {
    background: var(--bg-card);
    border: 1px solid var(--border-color);
    border-radius: var(--border-radius);
    padding: var(--spacing-md);
    text-align: center;
    transition: var(--transition);
    display: block;
    text-decoration: none;
  }
  .cert-badge:hover {
    border-color: var(--accent-secondary);
    box-shadow: 0 0 15px rgba(0, 229, 255, 0.15);
    transform: translateY(-3px);
  }
  .cert-logo {
    font-size: 2.2rem;
    margin-bottom: var(--spacing-xs);
    color: var(--accent-secondary);
  }
  .cert-name {
    font-size: 0.9rem;
    font-weight: 700;
    color: var(--text-primary);
    margin-bottom: 2px;
  }
  .cert-org {
    font-size: 0.75rem;
    color: var(--text-muted);
  }
</style>

<!-- Cyber HUD Hero Section -->
<section class="hero" style="padding-bottom: var(--spacing-lg);">
  <div class="container">
    <div class="cyber-hud-container">
      <h1 class="hero-title" style="margin-bottom: 5px; text-shadow: 0 0 15px rgba(0, 255, 102, 0.3);">🛡️ VulnQuest</h1>
      <p class="hero-subtitle" style="font-size: 1.25rem; font-family: var(--font-mono); color: var(--accent-primary);">[ OFFENSIVE SECURITY OPERATIONS ]</p>
      
      <p class="hero-description" style="max-width: 800px; margin: var(--spacing-md) auto var(--spacing-lg); font-size: 1rem;">
        Exploring the architecture of networks, systems, and APIs through live Bug Bounty hunts, Red Team simulations, custom vulnerability tools development, and security sandbox configurations.
      </p>
      
      <div class="hero-buttons">
        <a href="{{ '/bugbounty/' | relative_url }}" class="btn btn-primary">
          <i class="fas fa-bug"></i> Bug Bounty Hub
        </a>
        <a href="{{ '/tools/' | relative_url }}" class="btn btn-secondary">
          <i class="fas fa-tools"></i> Explore Toolkit
        </a>
      </div>
      
      <div class="hud-telemetry">
        <div class="hud-item">SYS_STATUS: <span>ACTIVE_OPERATIONAL</span></div>
        <div class="hud-item">TARGET_SCOPE: <span>COMPREHENSIVE_AUDIT</span></div>
        <div class="hud-item">IP_ROUTING: <span>TUNNEL_SECURE_TLS</span></div>
        <div class="hud-item">ACTIVE_LABS: <span>4_ENVIRONMENTS</span></div>
      </div>
    </div>
  </div>
</section>

<!-- Operations Stats Dashboard -->
<section class="section" style="margin-bottom: var(--spacing-lg);">
  <div class="container">
    <h2 class="section-title">Operations Metrics</h2>
    <div class="stats-dashboard">
      <div class="stat-card">
        <div class="stat-val">42</div>
        <div class="stat-lbl">Severe Bugs Reported</div>
      </div>
      <div class="stat-card">
        <div class="stat-val">Top 1%</div>
        <div class="stat-lbl">HackTheBox Ranking</div>
      </div>
      <div class="stat-card">
        <div class="stat-val">5</div>
        <div class="stat-lbl">Custom Repositories</div>
      </div>
      <div class="stat-card">
        <div class="stat-val">30+</div>
        <div class="stat-lbl">Active Lab Instances</div>
      </div>
    </div>
  </div>
</section>

<!-- Focus Areas Grid -->
<section class="section">
  <div class="container">
    <h2 class="section-title">Cyber Specialties</h2>
    <div class="cards-grid">
      
      <div class="card">
        <div class="card-icon"><i class="fas fa-bug"></i></div>
        <h3 class="card-title">Bug Bounty</h3>
        <p class="card-description">
          Methodical vulnerability hunting targeting API structures, file upload mechanisms, and access controls.
        </p>
        <a href="{{ '/bugbounty/' | relative_url }}" class="card-link">
          Explore Hub <i class="fas fa-arrow-right"></i>
        </a>
      </div>
      
      <div class="card">
        <div class="card-icon"><i class="fas fa-user-ninja"></i></div>
        <h3 class="card-title">Red Teaming</h3>
        <p class="card-description">
          Simulating real-world adversaries using modular command-and-control, evasions, and lateral steps.
        </p>
        <a href="{{ '/redteam/' | relative_url }}" class="card-link">
          Explore Red Team <i class="fas fa-arrow-right"></i>
        </a>
      </div>
      
      <div class="card">
        <div class="card-icon"><i class="fas fa-tools"></i></div>
        <h3 class="card-title">Tools Engineering</h3>
        <p class="card-description">
          Developing bespoke offensive scripts, custom provisioners, and binary trace frameworks.
        </p>
        <a href="{{ '/tools/' | relative_url }}" class="card-link">
          Explore Tools <i class="fas fa-arrow-right"></i>
        </a>
      </div>
      
      <div class="card">
        <div class="card-icon"><i class="fas fa-flag"></i></div>
        <h3 class="card-title">CTF Writeups</h3>
        <p class="card-description">
          Solutions cataloging systems compromises and logical breakdowns across key CTF platforms.
        </p>
        <a href="{{ '/ctf/' | relative_url }}" class="card-link">
          Explore CTF <i class="fas fa-arrow-right"></i>
        </a>
      </div>
      
      <div class="card">
        <div class="card-icon"><i class="fas fa-flask"></i></div>
        <h3 class="card-title">Security Labs</h3>
        <p class="card-description">
          Detailed sandboxes mimicking real corporate networks, AD forests, and cloud structures.
        </p>
        <a href="{{ '/labs/' | relative_url }}" class="card-link">
          Explore Labs <i class="fas fa-arrow-right"></i>
        </a>
      </div>
      
      <div class="card">
        <div class="card-icon"><i class="fas fa-blog"></i></div>
        <h3 class="card-title">Research Blog</h3>
        <p class="card-description">
          Documenting findings, cheatsheets, configuration blueprints, and security studies.
        </p>
        <a href="{{ '/blog/' | relative_url }}" class="card-link">
          Read Blog <i class="fas fa-arrow-right"></i>
        </a>
      </div>
      
    </div>
  </div>
</section>

<!-- Industry Certifications Dashboard -->
<section class="section" style="margin-bottom: var(--spacing-lg);">
  <div class="container">
    <h2 class="section-title">Professional Credentials</h2>
    <div class="certs-grid">
      
      <!-- OSCP -->
      <a href="{{ '/certifications/oscp/' | relative_url }}" class="cert-badge">
        <div class="cert-logo">🏆</div>
        <div class="cert-name">OSCP</div>
        <div class="cert-org">OffSec Certified Professional</div>
      </a>
      
      <!-- OSEP -->
      <a href="{{ '/certifications/osep/' | relative_url }}" class="cert-badge">
        <div class="cert-logo">🛡️</div>
        <div class="cert-name">OSEP</div>
        <div class="cert-org">OffSec Evasion & Security</div>
      </a>
      
      <!-- OSWE -->
      <a href="{{ '/certifications/oswe/' | relative_url }}" class="cert-badge">
        <div class="cert-logo">💻</div>
        <div class="cert-name">OSWE</div>
        <div class="cert-org">OffSec Web Expert</div>
      </a>
      
      <!-- CRTO -->
      <a href="{{ '/certifications/crto/' | relative_url }}" class="cert-badge">
        <div class="cert-logo">🎯</div>
        <div class="cert-name">CRTO</div>
        <div class="cert-org">Certified Red Team Operator</div>
      </a>
      
      <!-- PNPT -->
      <a href="{{ '/certifications/pnpt/' | relative_url }}" class="cert-badge">
        <div class="cert-logo">⚔️</div>
        <div class="cert-name">PNPT</div>
        <div class="cert-org">Practical Network Penetration Tester</div>
      </a>
      
      <!-- eWPTX -->
      <a href="{{ '/certifications/ewptx/' | relative_url }}" class="cert-badge">
        <div class="cert-logo">⚡</div>
        <div class="cert-name">eWPTX</div>
        <div class="cert-org">eLearn Web Application Tester</div>
      </a>
      
      <!-- CRT -->
      <a href="{{ '/certifications/crt/' | relative_url }}" class="cert-badge">
        <div class="cert-logo">📡</div>
        <div class="cert-name">CRT</div>
        <div class="cert-org">CREST Registered Tester</div>
      </a>
      
      <!-- CEH Practical -->
      <a href="{{ '/certifications/ceh-practical/' | relative_url }}" class="cert-badge">
        <div class="cert-logo">🔬</div>
        <div class="cert-name">CEH Practical</div>
        <div class="cert-org">Certified Ethical Hacker</div>
      </a>
      
    </div>
  </div>
</section>

<!-- Latest Dynamic Articles Feed -->
<section class="section">
  <div class="container">
    <h2 class="section-title">Latest Updates</h2>
    <div class="cards-grid">
      {% for post in site.posts limit:3 %}
        <div class="card">
          <div class="card-icon"><i class="fas fa-newspaper" style="color: var(--accent-secondary);"></i></div>
          <h3 class="card-title">{{ post.title }}</h3>
          <p class="card-description">{{ post.excerpt | strip_html | truncate: 140 }}</p>
          <a href="{{ post.url | relative_url }}" class="card-link">
            Read More <i class="fas fa-arrow-right"></i>
          </a>
        </div>
      {% endfor %}
    </div>
  </div>
</section>
