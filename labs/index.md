---
layout: page
title: Security Labs
subtitle: Custom vulnerable environments, active directory forests, and cloud infrastructures
description: "Sleek practice laboratories covering Active Directory, Web Apps, Cloud Security, and Mobile Instrumentation."
permalink: /labs/
---

## 🔬 Security Practice Laboratories

Welcome to my security laboratories portal. I maintain a series of local, cloud, and containerized networks to test exploit payloads, model advanced attack vectors, and practice configuration auditing. 

Each lab is built using infrastructure-as-code principles (Vagrant, Docker, and Ansible) to ensure reproducible, clean environments for security research.

---

<div class="cards-grid">

  <!-- Active Directory Lab -->
  <div class="card" style="border: 1px solid var(--accent-primary);">
    <div class="card-icon">🌲</div>
    <h3 class="card-title">Active Directory Lab</h3>
    <p class="card-description">
      Local forest environment featuring domain controllers, certificate servers (AD CS), and trust relations to model enterprise attack paths.
    </p>
    <a href="{{ '/labs/ad-labs/' | relative_url }}" class="card-link">Explore AD Lab →</a>
  </div>

  <!-- Web Application Lab -->
  <div class="card">
    <div class="card-icon">🌐</div>
    <h3 class="card-title">Web Application Lab</h3>
    <p class="card-description">
      Docker-compose stacks running vulnerable backend services (Node.js, Python, PHP) to safely audit API flaws and server-side injection vectors.
    </p>
    <a href="{{ '/labs/web-labs/' | relative_url }}" class="card-link">Explore Web Lab →</a>
  </div>

  <!-- Cloud Infrastructure Lab -->
  <div class="card">
    <div class="card-icon">🌩️</div>
    <h3 class="card-title">Cloud Infrastructure</h3>
    <p class="card-description">
      Isolated AWS & Azure staging deployments featuring misconfigured IAM roles, metadata exposures, and serverless privilege escalation paths.
    </p>
    <a href="{{ '/labs/cloud-labs/' | relative_url }}" class="card-link">Explore Cloud Lab →</a>
  </div>

  <!-- Mobile Security Lab -->
  <div class="card">
    <div class="card-icon">📱</div>
    <h3 class="card-title">Mobile Security Lab</h3>
    <p class="card-description">
      Rooted Android and jailbroken iOS endpoints preconfigured with Frida instrumentation servers to audit local storage and bypass SSL pinning.
    </p>
    <a href="{{ '/labs/mobile-labs/' | relative_url }}" class="card-link">Explore Mobile Lab →</a>
  </div>

</div>

---

## 📊 Lab Infrastructure Statistics

Below is an overview of the system resource allocations and orchestrations powering these practice networks:

| Environment | Hosts / Containers | Hypervisor / Cloud | Orchestration Tool |
| :--- | :--- | :--- | :--- |
| **Active Directory** | 4 Windows VMs | VMware ESXi | Vagrant + PowerShell DSC |
| **Web Security** | 12 Docker Containers | Local Docker Host | Docker-Compose + Ansible |
| **Cloud Labs** | EKS Cluster, 3 VMs | AWS & Azure Sandbox | Terraform |
| **Mobile Labs** | Pixel 4a, iPhone 8 | Physical / Corellium | custom dynamic instrumentation |

---

## 🛠️ Orchestration Blueprint

My custom lab provisioning engine, **Lab Manager**, is used to orchestrate these environments on demand. You can find detailed provisioning scripts, network configs, and deployment guides in the [Lab Manager Wiki]({{ '/tools/lab-manager/' | relative_url }}) under the Tools section.
