---
layout: page
title: Havoc C2 Configuration
subtitle: Modern C++ post-exploitation framework setup
permalink: /redteam/c2-frameworks/havoc/
---

## Havoc C2 Framework

Havoc is a modern, customizable post-exploitation framework designed by C5pider. Its primary agent, the Demon, is written in C++ and assembly, featuring state-of-the-art EDR evasion techniques.

### Server & Client Setup

We host the Havoc Teamserver on a Debian server. The configuration file `havoc.yaotl` defines IP bindings and operators:

```toml
# Teamserver configuration snippet
[Teamserver]
Host = "0.0.0.0"
Port = 40056

[Operators]
"operator58" = "SecurePBKDF2PasswordHash"
```

To run the teamserver:

```bash
./havoc server --profile havoc.yaotl -v
```

---

## Demon Agent Features & Customization

The Demon agent uses several stealth mechanisms to bypass detection:

*   **Sleep Obfuscation**: Uses Ekko or Z0ne memory protection techniques to encrypt its memory space during sleep, leaving it undetectable by scanner tools like `Moneta` or `PE-Sieve`.
*   **System Calls**: Uses direct or indirect syscalls dynamically resolved at runtime to bypass API hooks placed by EDRs on NTDLL functions (like `NtAllocateVirtualMemory`).
*   **Payload Customization**:
    *   Implant type: Executable (EXE) or Dynamic Link Library (DLL).
    *   Injection: Configured to use Custom Thread Start or Thread APC hijacking.

### Configuring Listeners
We configure a secure HTTPS listener inside the Havoc GUI client console, specifying user agent parameters matching standard Chrome traffic to mask network communications.
