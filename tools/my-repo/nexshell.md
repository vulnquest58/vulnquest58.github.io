---
layout: default
title: NexShell — Elite Reverse Shell Commander
description: Cross-platform reverse shell handler with Shell Intelligence, 15+ payload types, AMSI bypass, AD Recon, Persistence, Container Escape, and Lateral Movement modules.
---

<div class="tool-page">

<!-- ── Hero ───────────────────────────────────────────────────────────────── -->
<div class="tool-hero">
  <div class="tool-hero-icon">🐚</div>
  <div class="tool-hero-info">
    <h1 class="tool-title">NexShell</h1>
    <p class="tool-subtitle">Elite Reverse Shell Commander · Nexus of Shell Operations</p>
    <div class="tool-badges">
      <span class="badge badge-purple">Python 3.6+</span>
      <span class="badge badge-lime">No Dependencies</span>
      <span class="badge badge-cyan">Linux · Windows · macOS</span>
      <span class="badge badge-orange">v1.0.0</span>
    </div>
    <div class="tool-links">
      <a href="https://github.com/vulnquest58/nexshell" class="btn btn-primary" target="_blank">
        <svg width="16" height="16" fill="currentColor" viewBox="0 0 24 24"><path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0 0 24 12c0-6.63-5.37-12-12-12z"/></svg>
        GitHub
      </a>
      <a href="#installation" class="btn btn-secondary">Installation</a>
      <a href="#modules" class="btn btn-secondary">Modules</a>
    </div>
  </div>
</div>

<!-- ── What is NexShell ────────────────────────────────────────────────────── -->
<section class="tool-section">
  <h2>What is NexShell?</h2>
  <p>
    NexShell is an <strong>elite, cross-platform reverse shell commander</strong> designed for penetration testers and red teamers who demand more than a simple netcat listener.
    It replaces the entire post-connection workflow — from shell stabilization to privilege escalation — in a single, dependency-free Python script.
  </p>
  <p>
    Built on the architecture of <a href="https://github.com/brightio/penelope" target="_blank">penelope</a> and extended with a complete operational module suite targeting both Linux and Windows environments, including Active Directory.
  </p>

  <div class="info-grid">
    <div class="info-card">
      <div class="info-icon">🧠</div>
      <h3>Shell Intelligence</h3>
      <p>Auto-detects target OS, shell type (dumb → PTY), and privilege level on connect. Prompt changes color on root/SYSTEM.</p>
    </div>
    <div class="info-card">
      <div class="info-icon">🎯</div>
      <h3>Payload Arsenal</h3>
      <p>15+ reverse shell payloads for Linux and Windows. Base64/hex obfuscation. AMSI bypass variants. LOLBins (MSHTA, WMIC, Regsvr32).</p>
    </div>
    <div class="info-card">
      <div class="info-icon">🔍</div>
      <h3>Recon Modules</h3>
      <p>QuickEnum, PrivEsc Advisor, CredHarvest — all run in-memory (no disk writes). Windows equivalents powered by PowerShell.</p>
    </div>
    <div class="info-card">
      <div class="info-icon">🏛️</div>
      <h3>AD Attack Chain</h3>
      <p>No BloodHound, no SharpHound needed. Native PowerShell AD recon: domain info, Kerberoast targets, ASREPRoast, delegation.</p>
    </div>
  </div>
</section>

<!-- ── Feature Matrix ─────────────────────────────────────────────────────── -->
<section class="tool-section" id="features">
  <h2>Feature Matrix</h2>

  <div class="table-wrapper">
    <table>
      <thead>
        <tr>
          <th>Feature</th>
          <th>🐧 Linux</th>
          <th>🪟 Windows</th>
          <th>🍎 macOS</th>
        </tr>
      </thead>
      <tbody>
        <tr><td>Auto PTY upgrade</td><td>✅</td><td>✅ ConPtyShell</td><td>✅</td></tr>
        <tr><td>Shell quality score</td><td>✅</td><td>✅</td><td>✅</td></tr>
        <tr><td>OS + privilege detection</td><td>✅</td><td>✅</td><td>✅</td></tr>
        <tr><td>Session logging</td><td>✅</td><td>✅</td><td>✅</td></tr>
        <tr><td>In-memory module execution</td><td>✅ bash</td><td>✅ PowerShell</td><td>✅</td></tr>
        <tr><td>Jitter / stealth mode</td><td>✅</td><td>✅</td><td>✅</td></tr>
        <tr><td>Session tags + notes</td><td>✅</td><td>✅</td><td>✅</td></tr>
        <tr><td>Multi-session + multi-listener</td><td>✅</td><td>✅</td><td>✅</td></tr>
        <tr><td>AMSI bypass</td><td>—</td><td>✅ 4 variants</td><td>—</td></tr>
        <tr><td>LOLBin payloads</td><td>—</td><td>✅ MSHTA/WMIC/Regsvr32</td><td>—</td></tr>
        <tr><td>AD Recon (no tools)</td><td>—</td><td>✅</td><td>—</td></tr>
        <tr><td>Container escape</td><td>✅ Docker/K8s</td><td>—</td><td>—</td></tr>
      </tbody>
    </table>
  </div>
</section>

<!-- ── Installation ───────────────────────────────────────────────────────── -->
<section class="tool-section" id="installation">
  <h2>Installation</h2>

  <div class="tab-group">
    <div class="tab-header">
      <button class="tab-btn active" onclick="showTab(event,'linux-tab')">Linux / Kali</button>
      <button class="tab-btn" onclick="showTab(event,'windows-tab')">Windows</button>
      <button class="tab-btn" onclick="showTab(event,'standalone-tab')">Standalone</button>
    </div>

    <div id="linux-tab" class="tab-content active">
<div class="code-block">
<pre><code># Clone and install system-wide
git clone https://github.com/vulnquest58/nexshell
cd nexshell
chmod +x setup.sh && ./setup.sh install

# Or add alias (Kali/Parrot)
echo 'alias nexshell="python3 ~/.tools/nexshell/nexshell.py"' >> ~/.zshrc</code></pre>
</div>
    </div>

    <div id="windows-tab" class="tab-content">
<div class="code-block">
<pre><code># PowerShell (WSL2 recommended for full PTY support)
git clone https://github.com/vulnquest58/nexshell
cd nexshell
python nexshell.py

# Or create a permanent alias
Set-Alias nexshell "python3 C:\tools\nexshell\nexshell.py"</code></pre>
</div>
    </div>

    <div id="standalone-tab" class="tab-content">
<div class="code-block">
<pre><code># No installation needed — zero dependencies
wget https://raw.githubusercontent.com/vulnquest58/nexshell/main/nexshell.py
python3 nexshell.py</code></pre>
</div>
    </div>
  </div>
</section>

<!-- ── Quick Start ────────────────────────────────────────────────────────── -->
<section class="tool-section" id="quickstart">
  <h2>Quick Start</h2>

  <div class="code-block">
<pre><code class="language-bash"># Listen on 4444 (default)
nexshell

# Multiple ports
nexshell -p 4444,5555,9001

# Show ALL payloads — Linux + Windows
nexshell -a

# Linux-only payloads
nexshell -a --linux

# Windows payloads with obfuscation (base64)
nexshell -a --windows --obfuscate

# Show AMSI bypass snippets
nexshell --amsi

# Connect to a bind shell
nexshell -c 10.10.10.10 -p 4444

# Enable stealth (jitter + in-memory only)
nexshell --stealth --jitter 300

# Auto-run QuickEnum on every new shell
nexshell --auto-enum</code></pre>
  </div>
</section>

<!-- ── Modules ────────────────────────────────────────────────────────────── -->
<section class="tool-section" id="modules">
  <h2>Operational Modules</h2>
  <p>All modules run <strong>in-memory</strong> — nothing is written to disk on the target. Linux modules use bash, Windows modules use PowerShell <code>-enc</code>.</p>

  <!-- Recon -->
  <h3>🔍 Recon</h3>
  <div class="module-grid">
    <div class="module-card linux">
      <div class="module-os">🐧 Linux</div>
      <h4>quickenum</h4>
      <p>OS info, current user, sudo rights, SUID binaries, cron jobs, network interfaces, open ports, interesting files, SSH keys.</p>
      <code>run quickenum</code>
    </div>
    <div class="module-card windows">
      <div class="module-os">🪟 Windows</div>
      <h4>win-enum</h4>
      <p>System info, local admins, network interfaces, open ports, running processes, AV/EDR detection, shares, domain membership.</p>
      <code>run win-enum</code>
    </div>
  </div>

  <!-- PrivEsc -->
  <h3>⬆️ Privilege Escalation</h3>
  <div class="module-grid">
    <div class="module-card linux">
      <div class="module-os">🐧 Linux</div>
      <h4>privesc</h4>
      <p>SUID/GTFOBins, capabilities, writable PATH, writable service files, NFS no_root_squash, Docker socket, LXD membership.</p>
      <code>run privesc</code>
    </div>
    <div class="module-card windows">
      <div class="module-os">🪟 Windows</div>
      <h4>win-privesc</h4>
      <p>AlwaysInstallElevated, unquoted service paths, writable service binaries, scheduled tasks, token privileges, autologon.</p>
      <code>run win-privesc</code>
    </div>
  </div>

  <!-- Creds -->
  <h3>🔑 Credential Harvesting</h3>
  <div class="module-grid">
    <div class="module-card linux">
      <div class="module-os">🐧 Linux</div>
      <h4>credharvest</h4>
      <p>/etc/passwd, .env files, config files with passwords, database configs, history files, SSH authorized_keys.</p>
      <code>run credharvest</code>
    </div>
    <div class="module-card windows">
      <div class="module-os">🪟 Windows</div>
      <h4>win-creds</h4>
      <p>SAM/SYSTEM dump attempt, Credential Manager, browser login databases (Chrome/Edge/Firefox), WinSCP sessions, PowerShell history, LAPS.</p>
      <code>run win-creds</code>
    </div>
  </div>

  <!-- AD -->
  <h3>🏛️ Active Directory</h3>
  <div class="module-grid">
    <div class="module-card windows">
      <div class="module-os">🪟 Windows</div>
      <h4>ad-recon</h4>
      <p>Domain info, domain controllers, privileged users, trust relationships. Pure PowerShell — no SharpHound needed.</p>
      <code>run ad-recon</code>
    </div>
    <div class="module-card windows">
      <div class="module-os">🪟 Windows</div>
      <h4>ad-kerberoast</h4>
      <p>Find all accounts with SPNs set — Kerberoastable targets. Lists samAccountName + SPN.</p>
      <code>run ad-kerberoast</code>
    </div>
    <div class="module-card windows">
      <div class="module-os">🪟 Windows</div>
      <h4>ad-asreproast</h4>
      <p>Find accounts with "Do not require Kerberos pre-authentication" — ASREPRoastable targets.</p>
      <code>run ad-asreproast</code>
    </div>
  </div>

  <!-- Persistence -->
  <h3>🔒 Persistence</h3>
  <div class="module-grid">
    <div class="module-card linux">
      <div class="module-os">🐧 Linux</div>
      <h4>persist (Linux)</h4>
      <p>Generates: crontab reverse shell, ~/.bashrc hook, SUID bash copy, authorized_keys injection, systemd service, rc.local.</p>
      <code>run persist</code>
    </div>
    <div class="module-card windows">
      <div class="module-os">🪟 Windows</div>
      <h4>persist (Windows)</h4>
      <p>Generates: HKCU Run key, Startup folder, scheduled task (SYSTEM), WMI event subscription.</p>
      <code>run persist</code>
    </div>
  </div>

  <!-- Lateral -->
  <h3>➡️ Lateral Movement</h3>
  <div class="module-grid">
    <div class="module-card linux">
      <div class="module-os">🐧 Linux</div>
      <h4>lateral (Linux)</h4>
      <p>SSH hop, SSH agent hijack, Docker socket escape, LXD container escape, NFS no_root_squash exploit.</p>
      <code>run lateral</code>
    </div>
    <div class="module-card windows">
      <div class="module-os">🪟 Windows</div>
      <h4>lateral (Windows)</h4>
      <p>SMB host discovery, WMI remote exec, DCOM lateral movement, Pass-the-Hash.</p>
      <code>run lateral</code>
    </div>
  </div>

  <!-- Container -->
  <h3>🐳 Container Escape</h3>
  <div class="module-grid">
    <div class="module-card linux">
      <div class="module-os">🐧 Linux</div>
      <h4>container</h4>
      <p>Environment detection, privileged container escape, Docker socket abuse, cgroups v1 (CVE-2022-0492), Kubernetes service account enumeration.</p>
      <code>run container</code>
    </div>
  </div>

  <!-- Exfil -->
  <h3>📤 Data Exfiltration</h3>
  <div class="module-grid">
    <div class="module-card linux">
      <div class="module-os">🐧 Linux</div>
      <h4>exfil (Linux)</h4>
      <p>HTTP GET params (base64), DNS tunneling, ICMP exfil, HTTP POST multipart.</p>
      <code>run exfil</code>
    </div>
    <div class="module-card windows">
      <div class="module-os">🪟 Windows</div>
      <h4>exfil (Windows)</h4>
      <p>HTTPS POST (PowerShell), SMB copy to attacker share, certutil base64 encode.</p>
      <code>run exfil</code>
    </div>
  </div>
</section>

<!-- ── AMSI Bypass ────────────────────────────────────────────────────────── -->
<section class="tool-section" id="amsi">
  <h2>AMSI Bypass</h2>
  <p>NexShell includes 4 built-in AMSI bypass variants for Windows targets running PowerShell with AMSI enabled:</p>

  <div class="code-block">
<pre><code class="language-bash"># Show all AMSI bypass variants
nexshell --amsi

# Output example:
# [patch_memory]    - SetValue amsiInitFailed = $true
# [force_error]     - Write invalid value to amsiContext
# [script_block]    - Obfuscated string concatenation bypass
# [com_object]      - COM object-based bypass</code></pre>
  </div>
</section>

<!-- ── Session Management ─────────────────────────────────────────────────── -->
<section class="tool-section" id="sessions">
  <h2>Session Management</h2>

  <div class="code-block">
<pre><code class="language-text"># List sessions with OS, shell type, user, tag, duration
(NexShell)> sessions

  ➤  10.10.11.5  ◆ ROOT  []
  ┌──────┬──────┬─────────┬──────┬──────┬────────────┐
  │  ID  │ Shell│   OS    │ User │ Tag  │  Duration  │
  ├──────┼──────┼─────────┼──────┼──────┼────────────┤
  │  1   │ PTY  │  Linux  │ root │  -   │  00:05:32  │
  │  2   │ Basic│ Windows │ user │ DC01 │  00:01:10  │
  └──────┴──────┴─────────┴──────┴──────┴────────────┘

# Tag a session for easy identification
(NexShell)> tag 2 "Domain Controller"

# Add a note
(NexShell)> note Password found in /etc/config.php → admin:P@ss123

# Select and interact
(NexShell)> use 1
(NexShell)─(Session [1] · root)> interact</code></pre>
  </div>
</section>

<!-- ── Architecture ───────────────────────────────────────────────────────── -->
<section class="tool-section" id="architecture">
  <h2>Architecture</h2>

  <div class="code-block">
<pre><code>nexshell/
├── nexshell.py          # Main engine — standalone, zero dependencies
│   ├── Core             # Session multiplexer (select() loop)
│   ├── TCPListener      # Multi-port listener
│   ├── Session          # Shell handler (PTY, logging, in-memory exec)
│   ├── PayloadGenerator # 15+ payloads + obfuscation
│   ├── ShellIntelligence# OS/privilege auto-detection
│   └── MainMenu         # Interactive CLI with TAB completion
├── modules/
│   ├── windows.py       # Windows payloads, AMSI bypass, PS scripts
│   └── ops.py           # Persistence, Lateral, AD, Container, Exfil
├── payloads/            # (extensible payload packs)
└── setup.sh             # Cross-platform installer</code></pre>
  </div>
</section>

<!-- ── Tips ───────────────────────────────────────────────────────────────── -->
<section class="tool-section" id="tips">
  <h2>Pro Tips</h2>

  <div class="tips-grid">
    <div class="tip-card">
      <h4>💡 Multi-Port Hunting</h4>
      <p>Run <code>nexshell -p 80,443,4444,8080</code> to listen on common ports simultaneously — great for bypassing firewalls.</p>
    </div>
    <div class="tip-card">
      <h4>💡 Stealth CTF Mode</h4>
      <p>Use <code>--stealth --jitter 200</code> to add randomized delays and avoid leaving traces on the target disk.</p>
    </div>
    <div class="tip-card">
      <h4>💡 Windows PTY</h4>
      <p>After getting a PowerShell shell, run <code>upgrade</code> to trigger ConPtyShell — a fully interactive PTY on Windows.</p>
    </div>
    <div class="tip-card">
      <h4>💡 AD Fast Path</h4>
      <p>On a Windows shell: <code>run ad-kerberoast</code> + <code>run ad-asreproast</code> to find crackable hashes in under 30 seconds.</p>
    </div>
  </div>
</section>

</div>

<!-- ── Styles ──────────────────────────────────────────────────────────────── -->
<style>
.tool-page { max-width: 1100px; margin: 0 auto; padding: 2rem 1rem; font-family: 'Inter', sans-serif; }

/* Hero */
.tool-hero { display: flex; gap: 2rem; align-items: flex-start; padding: 2.5rem; background: linear-gradient(135deg, #0f0f1a, #1a0a2e); border-radius: 16px; border: 1px solid rgba(139,92,246,0.3); margin-bottom: 3rem; }
.tool-hero-icon { font-size: 4rem; }
.tool-title { font-size: 2.5rem; font-weight: 800; background: linear-gradient(90deg, #a855f7, #06b6d4); -webkit-background-clip: text; -webkit-text-fill-color: transparent; margin: 0 0 0.25rem; }
.tool-subtitle { color: #94a3b8; margin: 0 0 1rem; font-size: 1.05rem; }
.tool-badges { display: flex; flex-wrap: wrap; gap: 0.5rem; margin-bottom: 1.2rem; }
.badge { padding: 0.25rem 0.75rem; border-radius: 20px; font-size: 0.78rem; font-weight: 600; }
.badge-purple { background: rgba(168,85,247,0.2); color: #a855f7; border: 1px solid rgba(168,85,247,0.4); }
.badge-lime   { background: rgba(132,204,22,0.15); color: #84cc16; border: 1px solid rgba(132,204,22,0.4); }
.badge-cyan   { background: rgba(6,182,212,0.15);  color: #06b6d4; border: 1px solid rgba(6,182,212,0.4); }
.badge-orange { background: rgba(249,115,22,0.15); color: #f97316; border: 1px solid rgba(249,115,22,0.4); }
.tool-links { display: flex; gap: 0.75rem; flex-wrap: wrap; }
.btn { padding: 0.5rem 1.25rem; border-radius: 8px; text-decoration: none; font-weight: 600; font-size: 0.9rem; display: flex; align-items: center; gap: 0.4rem; transition: all 0.2s; }
.btn-primary  { background: #7c3aed; color: #fff; border: 1px solid #7c3aed; }
.btn-primary:hover { background: #6d28d9; transform: translateY(-1px); }
.btn-secondary { background: rgba(255,255,255,0.05); color: #cbd5e1; border: 1px solid rgba(255,255,255,0.1); }
.btn-secondary:hover { background: rgba(255,255,255,0.1); }

/* Sections */
.tool-section { margin-bottom: 3rem; }
.tool-section h2 { font-size: 1.6rem; font-weight: 700; color: #e2e8f0; border-left: 3px solid #7c3aed; padding-left: 0.75rem; margin-bottom: 1.2rem; }
.tool-section h3 { font-size: 1.1rem; font-weight: 700; color: #94a3b8; margin: 1.5rem 0 0.75rem; }
.tool-section p { color: #94a3b8; line-height: 1.7; }
.tool-section a { color: #a78bfa; }

/* Info grid */
.info-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(230px, 1fr)); gap: 1rem; margin-top: 1.5rem; }
.info-card { background: rgba(255,255,255,0.03); border: 1px solid rgba(255,255,255,0.08); border-radius: 12px; padding: 1.25rem; }
.info-icon { font-size: 2rem; margin-bottom: 0.5rem; }
.info-card h3 { color: #e2e8f0; font-size: 1rem; margin: 0 0 0.5rem; }
.info-card p { font-size: 0.88rem; color: #64748b; margin: 0; }

/* Table */
.table-wrapper { overflow-x: auto; }
table { width: 100%; border-collapse: collapse; }
th { background: rgba(124,58,237,0.2); color: #a78bfa; padding: 0.75rem 1rem; text-align: left; font-size: 0.9rem; }
td { padding: 0.6rem 1rem; color: #94a3b8; font-size: 0.88rem; border-bottom: 1px solid rgba(255,255,255,0.05); }
tr:hover td { background: rgba(255,255,255,0.02); }

/* Tabs */
.tab-group { background: rgba(255,255,255,0.02); border: 1px solid rgba(255,255,255,0.08); border-radius: 12px; overflow: hidden; }
.tab-header { display: flex; border-bottom: 1px solid rgba(255,255,255,0.08); }
.tab-btn { padding: 0.75rem 1.25rem; background: none; border: none; color: #64748b; cursor: pointer; font-size: 0.9rem; font-weight: 600; transition: all 0.2s; }
.tab-btn.active, .tab-btn:hover { color: #a855f7; background: rgba(168,85,247,0.1); }
.tab-content { display: none; padding: 1rem; }
.tab-content.active { display: block; }

/* Code */
.code-block { background: #0d1117; border: 1px solid rgba(255,255,255,0.08); border-radius: 10px; overflow-x: auto; }
.code-block pre { margin: 0; padding: 1.25rem; }
.code-block code { color: #e2e8f0; font-family: 'Fira Code', 'Cascadia Code', monospace; font-size: 0.85rem; line-height: 1.6; }

/* Module grid */
.module-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 1rem; margin-bottom: 1rem; }
.module-card { background: rgba(255,255,255,0.03); border-radius: 10px; padding: 1.1rem 1.25rem; border: 1px solid; }
.module-card.linux   { border-color: rgba(132,204,22,0.25); }
.module-card.windows { border-color: rgba(6,182,212,0.25); }
.module-os { font-size: 0.75rem; font-weight: 700; text-transform: uppercase; letter-spacing: 0.05em; margin-bottom: 0.4rem; color: #64748b; }
.module-card h4 { color: #e2e8f0; font-size: 1rem; margin: 0 0 0.4rem; }
.module-card p { font-size: 0.84rem; color: #64748b; margin: 0 0 0.6rem; }
.module-card code { background: rgba(124,58,237,0.15); color: #a78bfa; padding: 0.2rem 0.5rem; border-radius: 4px; font-size: 0.8rem; }

/* Tips */
.tips-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(240px, 1fr)); gap: 1rem; }
.tip-card { background: rgba(255,255,255,0.02); border: 1px solid rgba(255,255,255,0.06); border-radius: 10px; padding: 1.1rem; }
.tip-card h4 { color: #e2e8f0; font-size: 0.95rem; margin: 0 0 0.4rem; }
.tip-card p { font-size: 0.84rem; color: #64748b; margin: 0; }
.tip-card code { color: #84cc16; }
</style>

<script>
function showTab(event, tabId) {
  document.querySelectorAll('.tab-content').forEach(t => { t.style.display = 'none'; t.classList.remove('active'); });
  document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
  document.getElementById(tabId).style.display = 'block';
  document.getElementById(tabId).classList.add('active');
  event.currentTarget.classList.add('active');
}
</script>
