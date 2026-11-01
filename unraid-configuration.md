# Unraid Configuration

## 1. Purpose

This document describes the Unraid host configuration used by **MATRiX — Malware Analysis & Threat Research Infrastructure (X)**.

Unraid is the primary operating system installed on the physical server. It manages the server's storage, Docker containers, virtual machines, and the underlying resources used by the cybersecurity lab.

## 2. Host Information

| Setting | Configuration |
|---|---|
| Server hostname | `ALPHA` |
| Operating system | Unraid OS |
| Unraid version | `7.1.4` |
| Installation type | Unraid OS Starter |
| Primary role | Storage, Docker, and VM host |

> Verify the Unraid version and license details against the current server before publishing changes to this document.

## 3. Hardware

| Component | Specification |
|---|---|
| CPU | Intel Core i5-14600K |
| Motherboard | Gigabyte H610M H V3 DDR4 |
| Memory | 32 GB DDR4 |
| Host graphics | Intel UHD 770 |
| Dedicated GPU | AMD Radeon RX 6400 4 GB |
| CPU cooler | Ant Esports ICE C400 |

The Intel integrated graphics are used for host display output. The dedicated AMD GPU is intended for passthrough to a virtual machine when required.

## 4. Storage Configuration

| Device | Capacity | Intended role |
|---|---:|---|
| SATA SSD | 256 GB | Unraid cache pool |
| NVMe SSD | 512 GB | Proxmox and general VM storage |
| HDD | 2 TB | Array data disk |
| HDD | 4 TB | Parity disk |

The NVMe device is divided into separate storage areas: approximately 120 GB allocated for Proxmox and approximately 350 GB intended for general virtual-machine storage. Actual usable capacity depends on partitioning and filesystem overhead.

### Storage notes

- The array provides bulk storage.
- The parity disk is intended to provide single-disk parity protection; it is not a backup.
- Cache storage is used for workloads configured to use the cache pool.
- VM storage is separated from general array data where configured.

## 5. Docker and Virtual Machines

The Unraid dashboard has shown Docker and VM management enabled.

### Docker

Services observed in the server dashboard include:

- Emby Server
- Brave container (currently shown stopped in the supplied dashboard screenshot)

Other containers may be added or removed as the environment changes. Keep this list updated to reflect the live configuration.

### Virtual machines

The dashboard has shown these lab or virtualization VMs:

- OWASP Broken Web Applications (BWA) — shown running
- Proxmox VE — shown stopped in the supplied dashboard screenshot

Planned or intended lab environments include:

- FLARE-VM — Windows malware-analysis environment
- Kali Linux or Parrot OS — penetration-testing environment

Record a VM as deployed only after confirming it exists and is configured on the server.

## 6. Networking and Remote Access

Tailscale is configured to provide private remote connectivity to the server.

- Server hostname shown in Tailscale: `Alpha`
- Remote access is intended for authorized devices.
- Do not publish private IP addresses, authentication details, access tokens, or private keys in this repository.

Network topology, bridges, firewall rules, and service exposure will be documented separately in `network-architecture.md`.

## 7. Shares and Data Organization

The supplied Unraid dashboard showed shares including:

- `Docs`
- `Download browser`
- `Games`
- `Malware Docs`
- `Pics`
- `VMs`

It also showed system and application shares such as `appdata`, `domains`, `isos`, `proxmox`, and `system`.

Share names and access permissions can change. Review the live Unraid Shares page before publishing a current inventory. Do not include personal files or sensitive share contents in screenshots.

## 8. Security and Administration

MATRiX is a private research environment. Apply these practices:

- Keep Unraid administration interfaces private and restrict access to trusted devices.
- Use strong, unique credentials.
- Do not expose management interfaces directly to the public internet.
- Keep the host, containers, and virtual machines updated.
- Use VM snapshots before risky lab changes where appropriate.
- Keep backups of important data and configuration.
- Use isolated lab networks for malware execution and intentionally vulnerable applications.
- Never execute unknown malware on the Unraid host.

## 9. Verification Checklist

Before treating this document as a complete record, verify the following from the current Unraid interface:

- [ ] Unraid version and license details
- [ ] Array disk and parity assignments
- [ ] Cache pool membership and filesystem
- [ ] NVMe partitioning and VM storage location
- [ ] Share names, storage settings, and access permissions
- [ ] Docker containers and their current status
- [ ] VM names, status, CPU/RAM allocation, and network configuration
- [ ] GPU assignment and passthrough configuration
- [ ] Tailscale access and network settings

## 10. Planned Documentation

Related MATRiX documentation:

- `hardware-setup.md` — physical server components and assembly
- `virtualization-architecture.md` — nested virtualization and VM design
- `network-architecture.md` — network interfaces, bridges, and remote access
- `security-isolation.md` — lab isolation and safe research practices

---

**Project:** MATRiX — Malware Analysis & Threat Research Infrastructure (X)  
**Document:** Unraid Configuration  
**Status:** Initial documentation; verify checklist items against the live server.
