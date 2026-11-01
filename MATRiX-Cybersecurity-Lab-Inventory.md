# MATRiX — Cybersecurity Lab Inventory

## Purpose

This inventory records the cybersecurity tools reported in the MATRiX lab. Tool versions and exact configurations should be added as they are verified.

## Kali Linux

| Tool | Primary purpose | Planned practical use |
|---|---|---|
| Nessus | Vulnerability scanning and assessment | Scan authorized lab targets; validate findings and document remediation |
| Burp Suite | Web application security testing proxy | Inspect HTTP/S requests and responses and test OWASP BWA in the isolated lab |
| Wireshark | Network protocol and packet analysis | Capture lab traffic, inspect protocols, and investigate suspicious connections |

## FLARE-VM

The project owner reports that the FLARE-VM environment has its analysis tools installed.

Planned tool categories include:

- **Static analysis:** PEStudio, CFF Explorer, Exeinfo, strings
- **Dynamic analysis and monitoring:** Procmon, Regshot, Sysmon
- **Reverse engineering/debugging:** IDA Pro, OllyDbg

The list above records tools previously identified for the lab; confirm exact installation and versions before treating every item as verified.

## Lab safety

- Scan and test only systems you own or have explicit authorization to assess.
- OWASP BWA is intentionally vulnerable. Keep it off the normal home LAN and move it to an isolated lab network before testing.
- Do not run broad Nessus scans against the home network without authorization and a clear scope.
- Use Burp Suite against the lab application, not unrelated websites.
- Capture only traffic you are authorized to monitor. Avoid collecting credentials or personal traffic.
- Keep malware samples inside the isolated analysis environment. Use snapshots and revert after exercises.
- Sanitize screenshots, packet captures, reports, IP addresses, hostnames, credentials, and tokens before publishing to GitHub.

## Current inventory status

- [x] Nessus — reported installed in Kali Linux
- [x] Burp Suite — reported installed in Kali Linux
- [x] Wireshark — reported installed in Kali Linux
- [x] FLARE-VM — owner reports the analysis toolset is installed
- [ ] Verify exact FLARE-VM tool list and versions
- [ ] Record Nessus edition/version and plugin update status
- [ ] Record Burp Suite edition/version
- [ ] Record Wireshark version
- [ ] Add sanitized screenshots or sample lab reports

## Suggested portfolio exercises

1. **Vulnerability assessment:** Scan OWASP BWA after isolating it; sanitize the report; manually validate selected findings.
2. **Web application testing:** Use Burp Suite against OWASP BWA; document evidence, impact, and remediation.
3. **Network analysis:** Capture controlled lab traffic in Wireshark; identify DNS, TCP, HTTP, and TLS behavior.
4. **Windows telemetry:** Use Sysmon and Procmon to observe a benign test program; document process, file, registry, and network activity.
5. **Malware analysis:** Begin with safe static triage of a sample in an isolated FLARE-VM snapshot before considering dynamic execution.

---

*Inventory reflects tools reported by the project owner. Exact versions and configurations have not yet been independently verified.*
