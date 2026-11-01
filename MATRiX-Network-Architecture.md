# MATRiX — Network Architecture & Lab Isolation

## Current network layout

The lab currently uses these network modes:

- **Kali Linux:** Bridged to the normal home LAN
- **OWASP Broken Web Applications (BWA):** Bridged to the normal home LAN
- **FLARE-VM:** NAT

```text
                     Normal Home LAN
                           |
                    +------+------+
                    |             |
                 Kali Linux    OWASP BWA
                 (Proxmox)     (Unraid)
                    |
             [Bridged networking]


                    NAT network
                         |
                      FLARE-VM
                      (Proxmox)
```

This is a logical overview. Exact bridge names, subnet addresses, NAT implementation, and firewall rules have not yet been recorded.

## Security assessment

<badge>Risk: High until BWA is isolated</badge>

### OWASP BWA — Bridged to home LAN

OWASP BWA is intentionally vulnerable. Because it is bridged to the normal home LAN, other devices on that LAN may be able to connect to its vulnerable services. This creates avoidable risk for personal devices and other home-network systems.

### Kali Linux — Bridged to home LAN

Kali is a security-testing distribution. Bridging it to the home LAN gives it network access to that LAN, subject to routing and firewall rules. Use it only for authorized testing and avoid scanning or testing unrelated home devices.

### FLARE-VM — NAT

NAT commonly allows outbound connectivity through the host or virtual network while limiting unsolicited inbound connections. NAT alone is not a complete malware-containment boundary.

## Recommended action before further lab exercises

1. **Stop the OWASP BWA VM for now** if you are not actively using it.
2. Move OWASP BWA from the normal home LAN to a dedicated isolated virtual network.
3. Connect Kali to that same isolated lab network when testing BWA. Do not bridge either VM to the home LAN for these exercises.
4. Keep FLARE-VM on a separate isolated network for malware analysis, preferably with no internet access by default.
5. Do not enable shared folders, clipboard, or host integration for live-malware exercises unless required and understood.
6. Do not configure internet port forwarding to any lab VM.
7. Use clean VM snapshots before exercises and revert afterward.

---
