---
layout: page
title: "Certification Guide: OSEP"
subtitle: "OffSec Certified Security Professional (OSEP)"
permalink: /certifications/osep/
---

## 🛡️ OffSec Certified Security Professional (OSEP)

The **OSEP** is an advanced certifications path by **OffSec** focusing on evasion and breaching corporate networks. It validates practical skills in designing custom payloads, bypassing anti-virus (AV) and Endpoint Detection and Response (EDR) software, and executing lateral movements across hardened Windows environments.

---

### 📋 Exam Specifications

*   **Format**: 48-hour practical proctored challenge.
*   **Reporting**: 24 hours post-exam to deliver a professional red-team engagement report.
*   **Passing Criteria**: Compromise the primary domain controller flag or gather 10 points per machine up to 100 points.
*   **Exam Targets**: A complex enterprise network containing multiple Active Directory domains, firewalls, detection solutions, and administrative boundaries.

---

### 🛠️ Core Skills Validated

1.  **Defense Evasion & Obfuscation**: Bypassing signature and heuristic analysis of AV/EDR. Designing custom C# and C++ programs utilizing shellcode encryption (AES/XOR) and API hashing.
2.  **Process Injection & Memory Hacking**: Injecting shellcode into legitimate processes (e.g. process hollowing, API hooking) and bypassing Microsoft's Antimalware Scan Interface (AMSI) and AppLocker.
3.  **Active Directory Forest Trusts**: Exploiting trust relationships between domains, executing child-to-parent domain transitions, and crafting Golden/Silver tickets.
4.  **Linux Evasion**: Configuring custom SSH tunnels, auditing Linux PAM modules, and exploiting container environments.
5.  **C2 Operations & Pivoting**: Running multi-hop pivoting channels (using tools like `Chisel`, `rpivot`, and custom redirects) to route control packets to internal segmented servers.

---

### 🔗 Back to Credentials
- [Return to Certifications Dashboard]({{ '/certifications/' | relative_url }})
