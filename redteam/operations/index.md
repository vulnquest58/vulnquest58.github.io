---
layout: page
title: Red Team Operations Log
subtitle: Anonymized engagement summaries and post-op timelines
permalink: /redteam/operations/
---

## Operations Overview

This section documents anonymized summaries of red team engagements, organized chronologically. All identifying information has been removed or altered to protect client confidentiality. These logs are shared for educational purposes only.

> **Note**: All operations were authorized. Full written permission from the target organization was obtained before any testing commenced.

---

## Operation: IRONGATE (2025 Q1)

**Scope**: Full-scope external and internal red team assessment against a hypothetical mid-size financial services firm ("FS-Corp").

**Objective**: Assess the organization's detection and response capability against a nation-state level adversary (APT29 emulation).

### Phase 1: External Reconnaissance (Days 1–5)

**OSINT Footprinting**:
- Enumerated email format via LinkedIn scraping (`firstname.lastname@fscorp.com`).
- Discovered 3 dev subdomains via certificate transparency logs (`dev.fscorp.com`, `staging-api.fscorp.com`, `vpn-test.fscorp.com`).
- Identified OWA (Outlook Web Access) accessible externally at `mail.fscorp.com`.

**Initial Access Vector — Phishing**:
- Crafted a lure email themed around a mandatory HR policy update.
- Payload: A Microsoft Word document with a remote template injection (`DOCX → RTF → VBA macro via template URL`).
- The template was hosted on an actor-controlled server mimicking SharePoint (`sharepoint-fscorp.msdocuments.net`).
- **Result**: 3 employees executed the macro. One returned a callback to our Sliver C2 listener.

### Phase 2: Host Enumeration & Lateral Movement (Days 6–12)

**Initial Foothold**:
- Obtained a low-privilege shell on `WS-029.corp.fscorp.local` (a finance department workstation).
- Ran BloodHound `SharpHound` ingestor to map Active Directory attack paths.

**Key Finding — Kerberos Delegation**:
- BloodHound identified `SRV-PRINT01.corp.fscorp.local` was trusted for **Unconstrained Delegation**.
- Coerced a DC connection using **PrinterBug** (via `SpoolSample.exe`):
  ```bash
  SpoolSample.exe DC01.corp.fscorp.local SRV-PRINT01.corp.fscorp.local
  ```
- Captured the Domain Controller machine TGT ticket from LSASS using `Rubeus`:
  ```bash
  Rubeus.exe monitor /interval:1 /nowrap
  ```
- Passed the captured TGT to impersonate the DC and perform **DCSync**:
  ```bash
  Rubeus.exe ptt /ticket:<Base64TGT>
  Mimikatz # lsadump::dcsync /domain:corp.fscorp.local /user:krbtgt
  ```

### Phase 3: Domain Dominance & Exfiltration (Days 13–18)

- Created a **Golden Ticket** using the extracted KRBTGT hash for persistent offline access.
- Identified a misconfigured DFS share containing SQL backups (unencrypted `.bak` files).
- Exfiltrated 500MB of sample data (as agreed in scope) over an encrypted HTTPS tunnel.
- Established **persistence** via a WMI Event Subscription triggered on system startup.

### Phase 4: Report & Debrief (Days 19–21)

**Critical Findings**:
1. Unconstrained Delegation on print server → Full domain compromise.
2. OWA accessible externally → Initial phishing vector.
3. Unencrypted SQL backups on DFS shares → Data breach risk.
4. No EDR or SIEM alerts triggered during 18-day operation.

**Remediation Recommendations Delivered**:
- Disable Unconstrained Delegation on all servers.
- Require MFA for OWA and all external access points.
- Encrypt all backup data at rest.
- Deploy enhanced logging and alerting via Splunk correlation rules.

---

## Operation: PHANTOM (2024 Q4)

**Scope**: Cloud-only red team against a SaaS startup's AWS environment.

**Objective**: Test whether attacker with valid employee credentials could escalate to full cloud account takeover.

### Summary

- **Initial Access**: Compromised employee laptop via credential stuffing against their AWS SSO portal.
- **Privilege Escalation**: Found the employee had `iam:PassRole` permission → launched a new EC2 instance with admin role attached.
- **Data Exfiltration**: Accessed S3 buckets containing customer PII records.
- **Impact**: Full AWS account takeover in under 4 hours. No CloudTrail alerting was configured.
- **Key Remediation**: Enforce IAM least-privilege, enable CloudTrail with anomaly detection, restrict `iam:PassRole` to specific trusted roles.
