---
layout: page
title: VULNTRACE
subtitle: Dynamic vulnerability analysis and code tracing utility
permalink: /tools/vulntrace/
---

## VULNTRACE

**VULNTRACE** is a custom-built dynamic analysis framework that maps program execution flows to identify memory corruption vulnerabilities, logical flaws, and insecure code paths. It integrates with Frida for runtime instrumentation and supports both Windows PE files and Linux ELF binaries.

<div class="tool-badges">
  <span class="badge badge-language">Python</span>
  <span class="badge badge-language">Frida</span>
  <span class="badge badge-language">C</span>
  <span class="badge badge-status badge-success">Active Development</span>
</div>

---

## Core Features

| Feature | Description |
|---|---|
| **API Call Tracing** | Hooks all Win32/POSIX API calls and logs arguments, return values, and call stacks. |
| **Memory Leak Detection** | Tracks all `malloc`/`HeapAlloc` calls and flags unfreed allocations at process exit. |
| **Taint Analysis** | Propagates a "taint" mark from user-controlled input and reports when tainted data reaches sensitive sinks (e.g., `strcpy`, `system`, `exec`). |
| **Coverage Mapping** | Records code coverage per module, generating a heatmap of executed vs. unexecuted basic blocks. |
| **Report Generation** | Outputs findings in JSON and HTML formats with source file correlation where symbols are available. |

---

## Architecture

```
┌─────────────────────────────────┐
│         VULNTRACE Core          │
│  ┌───────────┐  ┌────────────┐  │
│  │  Frida    │  │  Analysis  │  │
│  │  Agent    │  │  Engine    │  │
│  │ (JS/C)    │  │ (Python)   │  │
│  └─────┬─────┘  └─────┬──────┘  │
│        │              │         │
│  ┌─────▼──────────────▼──────┐  │
│  │       Event Bus (IPC)     │  │
│  └─────────────┬─────────────┘  │
│                │                │
│  ┌─────────────▼─────────────┐  │
│  │      Report Generator     │  │
│  │    (JSON / HTML Output)   │  │
│  └───────────────────────────┘  │
└─────────────────────────────────┘
```

---

## Usage

### Basic Analysis

```bash
# Trace all API calls for a Windows executable
python vulntrace.py --target ./target.exe --mode trace --output report.json

# Enable taint analysis from CLI arguments
python vulntrace.py --target ./parser --mode taint --source argv --output report.html

# Detect memory leaks
python vulntrace.py --target ./service.exe --mode leaks --timeout 30
```

### Configuration File (`vulntrace.yaml`)

```yaml
target: "./vulnerable_app.exe"
mode: full    # trace | taint | leaks | coverage | full
output:
  format: html
  path: "./reports/"
hooks:
  - "VirtualAlloc"
  - "CreateFile"
  - "WriteFile"
taint_sources:
  - type: "argument"
    index: 1
taint_sinks:
  - "strcpy"
  - "sprintf"
  - "system"
```

---

## Example Output

```json
{
  "target": "vulnerable_app.exe",
  "analysis_mode": "taint",
  "findings": [
    {
      "severity": "CRITICAL",
      "type": "Stack Buffer Overflow",
      "sink": "strcpy",
      "taint_source": "argv[1]",
      "stack_trace": [
        "0x004011a3 vulnerable_app!process_input",
        "0x004010de vulnerable_app!main"
      ],
      "recommendation": "Replace strcpy with strncpy and validate input length."
    }
  ]
}
```

---

## GitHub Repository

> 🔗 [github.com/vulnquest58/vulntrace](https://github.com/vulnquest58/vulntrace)

*Note: Public release pending final security review and documentation pass.*
