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

  /* --- Interactive Terminal Styling --- */
  .terminal-wrapper {
    margin: var(--spacing-2xl) 0;
  }
  .terminal-header-title {
    font-size: 1.25rem;
    margin-bottom: var(--spacing-md);
    font-family: var(--font-primary);
    color: var(--text-primary);
    display: flex;
    align-items: center;
    gap: var(--spacing-sm);
  }
  .terminal-box {
    background: #040807;
    border: 1px solid var(--accent-primary);
    border-radius: var(--border-radius-lg);
    box-shadow: 0 0 30px rgba(0, 255, 102, 0.15);
    font-family: var(--font-mono);
    font-size: 0.9rem;
    color: #00ff66;
    padding: var(--spacing-lg);
    position: relative;
    overflow: hidden;
  }
  .terminal-box::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(
      rgba(18, 16, 16, 0) 50%, 
      rgba(0, 0, 0, 0.25) 50%
    );
    background-size: 100% 4px;
    z-index: 2;
    pointer-events: none;
  }
  .terminal-topbar {
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-bottom: 1px solid rgba(0, 255, 102, 0.2);
    padding-bottom: var(--spacing-sm);
    margin-bottom: var(--spacing-md);
    font-size: 0.8rem;
    color: var(--text-muted);
  }
  .terminal-dots {
    display: flex;
    gap: 6px;
  }
  .terminal-dot {
    width: 10px;
    height: 10px;
    border-radius: 50%;
  }
  .dot-red { background: #ff5f56; }
  .dot-yellow { background: #ffbd2e; }
  .dot-green { background: #27c93f; }
  
  .terminal-output {
    height: 320px;
    overflow-y: auto;
    margin-bottom: var(--spacing-md);
    scroll-behavior: smooth;
    padding-right: var(--spacing-xs);
  }
  .terminal-output::-webkit-scrollbar {
    width: 6px;
  }
  .terminal-output::-webkit-scrollbar-thumb {
    background: rgba(0, 255, 102, 0.3);
    border-radius: 3px;
  }
  
  .terminal-input-line {
    display: flex;
    align-items: center;
    gap: var(--spacing-xs);
  }
  .terminal-prompt {
    color: var(--accent-secondary);
    white-space: nowrap;
  }
  .terminal-input {
    background: transparent;
    border: none;
    outline: none;
    color: var(--text-primary);
    font-family: var(--font-mono);
    font-size: 0.9rem;
    flex-grow: 1;
    width: 100%;
  }
  
  .terminal-deck {
    display: flex;
    flex-wrap: wrap;
    gap: var(--spacing-sm);
    margin-top: var(--spacing-md);
  }
  .term-btn {
    background: rgba(0, 255, 102, 0.05);
    border: 1px solid rgba(0, 255, 102, 0.3);
    border-radius: 4px;
    color: var(--accent-primary);
    font-family: var(--font-mono);
    font-size: 0.75rem;
    padding: 6px 12px;
    cursor: pointer;
    transition: var(--transition);
  }
  .term-btn:hover {
    background: rgba(0, 255, 102, 0.15);
    border-color: var(--accent-primary);
    box-shadow: 0 0 10px rgba(0, 255, 102, 0.2);
  }
  
  /* --- Certifications Styling --- */
  .certs-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
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
  }
  .cert-badge:hover {
    border-color: var(--accent-secondary);
    box-shadow: 0 0 15px rgba(0, 229, 255, 0.1);
    transform: translateY(-2px);
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

<!-- Interactive Shell Command Line Widget -->
<section class="section" style="margin-bottom: var(--spacing-lg);">
  <div class="container">
    <div class="terminal-wrapper">
      <h2 class="terminal-header-title">
        <i class="fas fa-terminal" style="color: var(--accent-primary);"></i> Operations Terminal Console
      </h2>
      <div class="terminal-box">
        <div class="terminal-topbar">
          <div class="terminal-dots">
            <span class="terminal-dot dot-red"></span>
            <span class="terminal-dot dot-yellow"></span>
            <span class="terminal-dot dot-green"></span>
          </div>
          <div class="terminal-title">guest@vulnquest: ~</div>
          <div>bash</div>
        </div>
        <div class="terminal-output" id="termOutput">
          <div>Initializing VulnQuest secure shell console...</div>
          <div>Connection established. Type <span style="color: #e1ece7;">help</span> or click the deck below to run commands.</div>
          <br>
        </div>
        <div class="terminal-input-line">
          <span class="terminal-prompt">guest@vulnquest:~$</span>
          <input type="text" class="terminal-input" id="termInput" autocomplete="off" placeholder="Enter command..." />
        </div>
      </div>
      
      <!-- Command Quick Action Deck -->
      <div class="terminal-deck">
        <button class="term-btn" onclick="runShellCmd('help')">help</button>
        <button class="term-btn" onclick="runShellCmd('about')">about</button>
        <button class="term-btn" onclick="runShellCmd('skills')">skills</button>
        <button class="term-btn" onclick="runShellCmd('scan')">run_scan</button>
        <button class="term-btn" onclick="runShellCmd('stats')">metrics</button>
        <button class="term-btn" onclick="runShellCmd('clear')">clear</button>
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
      <div class="cert-badge">
        <div class="cert-logo">🎓</div>
        <div class="cert-name">OSCP</div>
        <div class="cert-org">OffSec Certified Professional</div>
      </div>
      <div class="cert-badge">
        <div class="cert-logo">🛡️</div>
        <div class="cert-name">OSEP</div>
        <div class="cert-org">OffSec Evasion & Security</div>
      </div>
      <div class="cert-badge">
        <div class="cert-logo">💻</div>
        <div class="cert-name">eWPTX</div>
        <div class="cert-org">eLearn Web Application Tester</div>
      </div>
      <div class="cert-badge">
        <div class="cert-logo">⚡</div>
        <div class="cert-name">CRT</div>
        <div class="cert-org">CREST Registered Tester</div>
      </div>
      <div class="cert-badge">
        <div class="cert-logo">🔬</div>
        <div class="cert-name">CEH Practical</div>
        <div class="cert-org">Certified Ethical Hacker</div>
      </div>
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

<!-- Terminal Simulator Script -->
<script>
  const outputEl = document.getElementById('termOutput');
  const inputEl = document.getElementById('termInput');

  // Input listener for custom user commands
  inputEl.addEventListener('keydown', function(e) {
    if (e.key === 'Enter') {
      const val = e.target.value.trim();
      e.target.value = '';
      if (val !== '') {
        executeCommand(val);
      }
    }
  });

  // Execute terminal command helper
  function runShellCmd(cmd) {
    executeCommand(cmd);
  }

  // Command routing logic
  function executeCommand(cmdStr) {
    // Append user query to prompt
    appendLine(`guest@vulnquest:~$ ${cmdStr}`, 'color: var(--accent-secondary);');
    
    const args = cmdStr.toLowerCase().split(' ');
    const cmd = args[0];
    
    switch(cmd) {
      case 'clear':
        outputEl.innerHTML = '';
        break;
      case 'help':
        printHelp();
        break;
      case 'about':
      case 'bio':
        printAbout();
        break;
      case 'skills':
        printSkills();
        break;
      case 'stats':
      case 'metrics':
        printStats();
        break;
      case 'scan':
      case 'run_scan':
        runMockScan();
        break;
      default:
        appendLine(`bash: command not found: ${cmd}. Type 'help' to view available operations.`, 'color: var(--accent-danger);');
    }
    
    // Auto scroll output window
    setTimeout(() => {
      outputEl.scrollTop = outputEl.scrollHeight;
    }, 50);
  }

  // Logging line creation helper
  function appendLine(text, style = '') {
    const line = document.createElement('div');
    if (style) {
      line.setAttribute('style', style);
    }
    line.innerHTML = text;
    outputEl.appendChild(line);
  }

  // --- Commmand Outputs ---
  function printHelp() {
    appendLine('Available operations inside the secure shell:', 'color: var(--text-secondary);');
    appendLine('  about  - Profile bio and operational focus details');
    appendLine('  skills - Cyber security skillset matrix metrics');
    appendLine('  scan   - Launch simulated multi-stage host vulnerability sweep');
    appendLine('  stats  - Retrieve platform metrics databases');
    appendLine('  clear  - Wipe current terminal output lines');
    appendLine('  help   - Print this help reference card');
  }

  function printAbout() {
    appendLine('=========================================', 'color: var(--accent-primary);');
    appendLine('🛡️ V U L N Q U E S T   P O R T F O L I O', 'color: var(--accent-primary); font-weight: bold;');
    appendLine('=========================================', 'color: var(--accent-primary);');
    appendLine('Security operations engineer specializing in high-impact vulnerability research and systems penetration testing.');
    appendLine('Focus Areas: Web API security, hybrid Active Directory exploit vectors, cloud security control systems auditing, and custom toolkit design.');
  }

  function printSkills() {
    appendLine('Loading capabilities audit matrix...', 'color: var(--text-muted);');
    setTimeout(() => {
      appendLine('Web Application Testing  [████████████░░] 85%', 'color: var(--accent-primary);');
      appendLine('Active Directory Audits  [█████████████░] 90%', 'color: var(--accent-primary);');
      appendLine('Cloud Security (AWS/AZ)  [██████████░░░░] 70%', 'color: var(--accent-primary);');
      appendLine('Mobile Apps Instrument   [███████████░░] 80%', 'color: var(--accent-primary);');
      appendLine('Software Tools Dev (Go)  [█████████████░] 90%', 'color: var(--accent-primary);');
    }, 150);
  }

  function printStats() {
    appendLine('Retrieving operational stats database...', 'color: var(--text-muted);');
    setTimeout(() => {
      appendLine('  • Disclosed Reports: 42 (HackerOne / Bugcrowd)');
      appendLine('  • HackTheBox Standing: Pro Hacker rank (Top 1% Global)');
      appendLine('  • Developed Wikis: 16 tool catalogs implemented');
      appendLine('  • Laboratory Nodes: 4 core virtualized segments');
    }, 150);
  }

  function runMockScan() {
    inputEl.disabled = true;
    appendLine('[+] Initializing network sweep engine...', 'color: var(--text-secondary);');
    
    setTimeout(() => {
      appendLine('[INFO] Scanning external namespaces on target.local using Subfinder...', 'color: var(--text-muted);');
    }, 500);

    setTimeout(() => {
      appendLine('[+] Harvested 6 active subdomain nodes from crt.sh certificate logs.', 'color: var(--accent-secondary);');
    }, 1200);

    setTimeout(() => {
      appendLine('[INFO] Executing Nuclei active scanner template sweeps...', 'color: var(--text-muted);');
    }, 1800);

    setTimeout(() => {
      appendLine('[CRITICAL] Vulnerability alert logged on portal.target.local: SSRF (AWS credentials leakage via IMDSv1).', 'color: var(--accent-danger); font-weight: bold;');
    }, 2600);

    setTimeout(() => {
      appendLine('[+] Sweeps completed successfully. Log outputs archived in target database.', 'color: var(--accent-primary);');
      inputEl.disabled = false;
      outputEl.scrollTop = outputEl.scrollHeight;
    }, 3200);
  }
</script>
