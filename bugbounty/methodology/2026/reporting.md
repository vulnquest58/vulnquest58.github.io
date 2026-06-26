---
layout: page
title: "2026 Methodology: Reporting"
subtitle: "CVSS v4.0 calculations and direct triage rules"
permalink: /bugbounty/methodology/2026/reporting/
---

## 📝 Next-Gen Reporting & Vulnerability Scores (2026)

Reporting in 2026 implements the latest industry scoring standards to evaluate vulnerabilities objectively and reduce triage overhead.

### 📊 CVSS v4.0 Metrics
We evaluate report severity using the CVSS v4.0 metrics, which provide a more granular assessment than CVSS v3.1:
- **Macro Vector**: Combines Base (Eq1), Environmental (Eq2), and Threat (Eq3) parameters to calculate the absolute score.
- **Supplemental Metrics**: Includes Safety, Automatable, Recovery, and Value Density to provide further context to security engineers.

### 📝 Report Outline
```markdown
# [Vulnerability Summary Title]

## Technical Description
Detailed layout of parameters, endpoints, and the specific payload.

## Steps to Reproduce
1. Step one...
2. Step two...

## Impact Assessment
Detailed CVSS v4.0 Base Score calculation and business scenario.

## Remediation Plan
Actionable configuration files or source code changes.
```

---

### 🔗 Navigation
- [Return to 2026 Dashboard]({{ '/bugbounty/methodology/2026/' | relative_url }})
- [Return to Methodology Hub]({{ '/bugbounty/methodology/' | relative_url }})


