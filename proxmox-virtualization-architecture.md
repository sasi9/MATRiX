# MATRiX — Proxmox Virtualization Architecture

## Overview

This document records the currently deployed virtual-machine layout in **MATRiX — Malware Analysis & Threat Research Infrastructure (X)**.

The physical server, **ALPHA**, runs Unraid. Proxmox VE runs as a nested virtual machine inside Unraid and manages the FLARE-VM and Kali Linux virtual machines. OWASP Broken Web Applications (BWA) runs separately as an Unraid-managed VM.

## Architecture

```text
Physical Server: ALPHA
└── Unraid OS
    ├── OWASP Broken Web Applications (BWA)
    │   └── Unraid-managed VM
    │
    └── Proxmox VE
        └── Nested VM hosted by Unraid
            ├── FLARE-VM
            └── Kali Linux
```

## VM resource allocation

| Virtual machine | Managed by | vCPU / cores allocated | RAM allocated | Virtual storage |
|---|---|---:|---:|---:|
| FLARE-VM | Proxmox VE | 6 | 8 GB | 100 GB |
| Kali Linux | Proxmox VE | 6 | 4 GB | 50 GB |
| OWASP BWA | Unraid | 2 | 1 GB | Not yet confirmed |

**Proxmox VE allocation:** 12 GB RAM was assigned to the Proxmox VE parent VM in Unraid.

## Lab purposes

### FLARE-VM
Windows-based malware-analysis environment for controlled static and dynamic analysis. Use isolated snapshots and avoid exposing samples or vulnerable services to the public internet.

### Kali Linux
Linux-based security testing environment for authorized network, web-application, and assessment exercises.

### OWASP BWA
Intentionally vulnerable web-application training environment. Keep it on an isolated lab network and test it only from systems you own or are authorized to use.

## Resource planning note

The two Proxmox guest VMs are currently assigned a combined **12 GB RAM**, while the parent Proxmox VM itself has **12 GB RAM** assigned by Unraid. This leaves no headroom inside the parent allocation for Proxmox overhead if both guests use their full allocations.

Consider increasing the RAM assigned to the Proxmox parent VM, if the Unraid host has sufficient available memory, or reducing the RAM assigned to one or both Proxmox guests.

The listed CPU counts are virtual CPU allocations, not proof that those cores are exclusively reserved for each VM.

## Safety and isolation

- Keep malware-analysis VMs isolated from production networks and personal devices.
- Use snapshots before executing or modifying samples.
- Do not bridge intentionally vulnerable machines directly to an untrusted or public network.
- Do not publish private IP addresses, hostnames, credentials, API keys, tokens, or sample files in this repository.
- Use only systems and applications for which you have explicit authorization.

## Verification checklist

- [x] Proxmox VE runs as a VM under Unraid.
- [x] FLARE-VM is deployed in Proxmox VE.
- [x] Kali Linux is deployed in Proxmox VE.
- [x] OWASP BWA runs as a separate Unraid-managed VM.
- [ ] Confirm OWASP BWA virtual disk size.
- [ ] Record the lab network mode and isolation controls.
- [ ] Add sanitized screenshots showing the VM inventory and settings.

---

*This document records the configuration details provided for the MATRiX lab. Update it whenever VM resources or placement change.*
