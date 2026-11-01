# MATRiX

### Malware Analysis & Threat Research Infrastructure (X)

**Self-Hosted Cybersecurity Research & Virtualization Environment**

------------------------------------------------------------------------

## Overview

MATRiX is a self-hosted infrastructure designed to support private data
storage, virtualization, malware analysis, threat intelligence,
penetration testing, and cybersecurity research.

I built this environment to reduce my dependence on third-party cloud
storage and online cybersecurity labs, while gaining practical
experience in deploying, managing, and securing my own infrastructure.

MATRiX provides a central platform for running virtual machines,
experimenting with security tools, investigating suspicious activity,
conducting authorized security testing, and developing cybersecurity
projects.

The environment supports **Red Team and Blue Team research**, with the
long-term goal of building a Purple Team workflow.

## Why I Built MATRiX

-   Keep greater control over my data and storage.
-   Build an independent cybersecurity research environment.
-   Deploy and manage isolated virtual machines.
-   Practice malware analysis and reverse engineering.
-   Perform authorized web application security testing.
-   Analyze network traffic and investigate suspicious activity.
-   Develop and test custom security automation tools.
-   Document practical research and project findings.

## Hardware Specifications

  Component       Specification
  --------------- ----------------------------------
  CPU             Intel Core i5-14600K
  Motherboard     Gigabyte H610M H V3 DDR4
  RAM             32 GB DDR4
  Host graphics   Intel UHD 770
  Dedicated GPU   AMD Radeon RX 6400 4 GB
  CPU cooler      Ant Esports ICE C400
  Case            Ant Esports Elite 1100 Mid-Tower
  Power supply    Ant Esports FP550B 550W

## Storage Architecture

  Storage device     Capacity Purpose
  ---------------- ---------- -------------------------------------
  SATA SSD             256 GB Unraid cache
  NVMe SSD             512 GB Proxmox and virtual machine storage
  HDD                    2 TB Unraid array
  HDD                    4 TB Parity

The NVMe storage is divided between Proxmox and general virtual machine
storage.

## Infrastructure Architecture

MATRiX uses Unraid as its primary host operating system. Proxmox VE runs
as a virtual machine on Unraid, providing an additional virtualization
layer for cybersecurity labs.

``` mermaid
flowchart TD
    A["Physical Server<br/>Intel Core i5-14600K · 32 GB RAM"]
    B["Unraid OS<br/>Primary Host"]
    C["Proxmox VE<br/>Nested Virtualization"]
    D["FLARE-VM<br/>Malware Analysis"]
    E["OWASP BWA<br/>Web Application Security Lab"]
    F["Kali Linux / Parrot OS<br/>Penetration Testing"]
    G["Docker Containers<br/>Self-Hosted Services"]
    H["Storage<br/>SSD · NVMe · HDD"]

    A --> B
    B --> C
    B --> G
    B --> H
    C --> D
    C --> E
    C --> F
```

## Virtualization & Cybersecurity Labs

### 1. FLARE-VM

A Windows-based environment for malware analysis and reverse
engineering.

Planned and ongoing activities:

-   Static and advanced static analysis.
-   Dynamic and behavioral analysis.
-   PE file inspection.
-   Process, file, and registry activity monitoring.
-   Malware behavior investigation.
-   Indicator of Compromise (IOC) extraction.
-   Mapping observed behavior to MITRE ATT&CK.

### 2. OWASP Broken Web Applications (BWA)

An intentionally vulnerable web application environment for learning and
authorized security testing.

Research areas:

-   SQL Injection.
-   Cross-Site Scripting (XSS).
-   Authentication and session-management weaknesses.
-   Web application security assessment.
-   Vulnerability validation and remediation.
-   Retesting to verify fixes.

### 3. Kali Linux / Parrot OS

Linux environments for offensive security research and authorized
penetration testing.

Research areas:

-   Network reconnaissance.
-   Vulnerability assessment.
-   Web application testing.
-   Network security testing.
-   Security automation using Python and Bash.

## Network & Remote Access

MATRiX uses Tailscale for private remote connectivity.

-   Private access to the infrastructure.
-   Remote administration from authorized devices.
-   Connectivity between supported devices and services.

Administrative interfaces are intended to remain private and accessible
only to authorized users.

## Self-Hosted Services

The server also provides a foundation for hosting personal applications
and services.

Examples include:

-   Docker-based applications.
-   Media services.
-   Private file storage and sharing.
-   Virtual machine storage.
-   Remote connectivity services.

The service inventory will be expanded as the infrastructure evolves.

## Cybersecurity Research Roadmap

### Red Team

-   Python and Bash security automation.
-   SQL Injection testing in authorized lab applications.
-   XSS testing and validation.
-   Web vulnerability assessment.
-   Burp Suite automation.
-   Vulnerability reporting and remediation guidance.

### Blue Team

-   Malware analysis and reverse engineering.
-   MITRE ATT&CK technique mapping.
-   Network traffic analysis using Wireshark.
-   Man-in-the-Middle attack detection research.
-   Windows event log analysis.
-   Detection engineering.
-   Incident investigation and reporting.

### Purple Team

-   Controlled attack simulation and detection validation.
-   Mapping attack activity to defensive detections.
-   Detection rule development and tuning.
-   Security control validation.
-   Automated testing and reporting.

## Security & Isolation

All offensive security testing is restricted to systems and applications
I own or have explicit permission to assess.

Malware analysis is performed in dedicated virtual machines and
controlled lab environments. Snapshots and isolation controls are used
where appropriate.

Credentials, access tokens, private keys, and sensitive network details
are not included in public documentation.

## Future Improvements

-   Centralized SIEM deployment.
-   IDS/IPS integration.
-   Automated malware analysis pipeline.
-   Network threat detection.
-   Custom Python security tools.
-   Automated vulnerability assessment.
-   Sigma detection rule development.
-   Centralized dashboards and infrastructure monitoring.

## Project Philosophy

**Build locally. Research independently. Test responsibly. Document
everything.**

MATRiX is an evolving infrastructure project focused on developing
practical cybersecurity skills through hands-on experimentation,
automation, and research.

------------------------------------------------------------------------

*Project: MATRiX --- Malware Analysis & Threat Research Infrastructure
(X)*
