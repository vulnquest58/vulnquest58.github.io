---
layout: page
title: "Specialty Guide: Reverse Engineering"
subtitle: "Decompilers, debuggers, static analysis tools, and malware sandboxes"
permalink: /tools/reverse-engineering/
---

## 🔬 Reverse Engineering (الهندسة العكسية)

This category collects disassemblers, decompilers, binary analysis utilities, system call tracers, and sandboxes designed to inspect compiled applications.

### Tool Catalog

<div class="vertical-cards-grid" style="display: flex; flex-direction: column; gap: var(--spacing-md); max-width: 800px; margin: var(--spacing-xl) 0;">

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🛠️</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Disassemblers & Decompilers</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Binary source reconstruction: <strong>Ghidra</strong> (NSA decompiler), <strong>IDA Pro</strong>, <strong>Binary Ninja</strong>, and <strong>Cutter</strong>.
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🐞</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Debuggers</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Instruction-level tracing: <strong>x64dbg</strong>, <strong>WinDbg</strong>, and <strong>GDB (with pwndbg/GEF/peda)</strong>.
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">⚙️</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Dynamic & Static Analysis</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Inspecting runtime properties: Windows Sysinternals <strong>ProcMon</strong>, <strong>DIE (Detect-It-Easy)</strong>, and <strong>PE-bear</strong>.
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🧪</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Malware Analysis</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Isolated checks: <strong>REMnux distro</strong>, <strong>Flare-VM</strong>, and automated sandboxes like <strong>Any.run</strong>.
      </p>
    </div>
  </div>

</div>

---

### 🔗 Back to Toolkit
- [Return to Main Tools Listing]({{ '/tools/' | relative_url }})
