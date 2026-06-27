---
layout: page
title: "Certification Guide: OSCP"
subtitle: "Offensive Security Certified Professional (OSCP)"
permalink: /certifications/oscp/
---

## 🏆 Offensive Security Certified Professional (OSCP)

The **OSCP** is the industry-standard credential for hands-on, practical penetration testing. Offered by **OffSec**, it validates a professional's capacity to perform reconnaissance, identify vulnerabilities, execute privilege escalations, and draft a comprehensive penetration testing report.

---

### 📋 Exam Specifications

*   **Format**: 24-hour practical exam proctored in a live virtual lab environment.
*   **Reporting**: 24 hours post-exam to submit a professional penetration testing report detailing replication steps, proof-of-concept codes, and remediation advice.
*   **Passing Criteria**: 70 points out of 100.
*   **Exam Targets**:
    *   **Active Directory Domain Set (40 Points)**: Composed of 1 Domain Controller and 2 Domain Clients. Requires full compromise of the domain forest.
    *   **Standalone Targets (3 x 20 Points)**: Three distinct machines requiring local user access (10 points) and root/system administrative privilege escalation (10 points).

---

### 🛠️ Core Skills Validated

1.  **Passive & Active Reconnaissance**: Using tools like `Nmap`, `Nikto`, and advanced directory listing scripts to identify open services and software versions.
2.  **Web Application Auditing**: Exploiting common vulnerabilities (SQL injections, Local File Inclusions, authentication bypasses, command injections).
3.  **Active Directory Exploitation**: Kerberoasting, AS-REP Roasting, domain enumeration (PowerView/BloodHound), pass-the-hash, and domain controller takeover.
4.  **Local Privilege Escalation**: Auditing Windows and Linux machines for weak service permissions, sudo privileges, cron job write access, kernel exploits, and configuration flaws.
5.  **Tunneling & Port Redirection**: Pivot routing through compromised nodes using `Chisel` or SSH local port forwarding.

---

### 🔗 Back to Credentials
- [Return to Certifications Dashboard]({{ '/certifications/' | relative_url }})
