---
layout: page
title: Kali Master Framework
subtitle: Automated Kali Linux setup and provisioning tool
permalink: /tools/kali-master/
---

## Kali Master

**Kali Master** is a fully automated Bash/Python provisioning framework that configures a fresh Kali Linux installation with a curated, organized set of offensive security tools, custom aliases, shell configuration, and personal tooling repositories — in a single command.

<div class="tool-badges">
  <span class="badge badge-language">Bash</span>
  <span class="badge badge-language">Python</span>
  <span class="badge badge-status badge-success">Active Development</span>
</div>

---

## Problem Statement

Setting up a new Kali environment manually is time-consuming and inconsistent. After a fresh install, a security professional must:
- Install dozens of tools manually.
- Configure `.bashrc`, `.zshrc`, tmux, vim/neovim.
- Clone and compile custom repositories.
- Set up API keys, VPN configs, and wordlists.

Kali Master automates **all of this in under 20 minutes**.

---

## Features

| Category | What Gets Configured |
|---|---|
| **Shell** | Zsh + Oh-My-Zsh + Powerlevel10k theme, custom aliases and functions |
| **Recon Tools** | subfinder, amass, httpx, nuclei, naabu, ffuf, gobuster, feroxbuster |
| **AD Tools** | BloodHound, Impacket suite, CrackMapExec, Evil-WinRM, Certipy |
| **C2 Tools** | Sliver, Havoc (compilation from source), Metasploit |
| **Web Tools** | Burp Suite Pro activation helper, SQLMap, Nikto, Arjun |
| **Post-Exploitation** | Mimikatz, Rubeus, SharpHound, PowerView, PowerSploit |
| **Wordlists** | SecLists, RockYou, assetnote wordlists via rsync |
| **VPN Setup** | Auto-configures HackTheBox and TryHackMe OpenVPN profiles |

---

## Installation

```bash
# Clone the repository
git clone https://github.com/vulnquest58/kali-master.git
cd kali-master

# Run the full setup (requires sudo)
sudo ./install.sh --profile full

# Run a minimal setup (recon tools only)
sudo ./install.sh --profile recon

# Install specific modules
sudo ./install.sh --modules ad,web,c2
```

---

## Profile Breakdown

```yaml
# profiles/full.yaml
profile: full
modules:
  - base_shell       # Zsh, tmux, neovim, fzf, bat
  - recon            # Subdomain, port scanning, HTTP probing tools
  - web_testing      # Web app testing suite
  - ad_attack        # Active Directory exploitation tools  
  - c2_framework     # Sliver, Havoc, Empire installation
  - post_exploit     # Mimikatz, Rubeus, PowerSploit
  - wordlists        # Download and organize wordlists
  - vpn_setup        # Configure HTB/THM VPN profiles
  - custom_aliases   # Personal shell aliases and functions
```

---

## Sample Output

```
[*] Kali Master v2.1.0 - Offensive Security Provisioning Tool
[*] Profile: full | Target: Kali Linux 2024.1

[✓] Base shell configuration complete (zsh + oh-my-zsh + powerlevel10k)
[✓] Recon tools installed: subfinder, amass, httpx, nuclei, naabu, ffuf
[✓] Web testing tools installed: burpsuite, sqlmap, nikto, arjun, feroxbuster  
[✓] AD tools installed: bloodhound, crackmapexec, impacket, certipy, evil-winrm
[✓] C2 frameworks compiled: sliver v1.5.42, empire v5.0.3
[✓] Post-exploitation tools: mimikatz, rubeus, sharphound, powerview
[✓] Wordlists downloaded: SecLists (8.2GB), RockYou, Assetnote
[✓] Custom aliases configured: 47 aliases, 12 functions
[✓] VPN profiles configured: HTB US East, THM US East

[+] Kali Master setup complete! Total time: 18m 43s
[+] Restart your terminal to apply all changes.
```

---

## GitHub Repository

> 🔗 [github.com/vulnquest58/kali-master](https://github.com/vulnquest58/kali-master)
