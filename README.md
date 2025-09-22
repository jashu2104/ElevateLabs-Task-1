# Task 1 — Local Network Port Scan (Nmap) And Packet Sniffing With Wireshark

## Overview
This repository contains the results and notes for **Task 1: Scan Your Local Network for Open Ports**.  
The network scanned: `192.168.1.0/24`. The raw Nmap output is in `scan_results.txt`.

**Scan performed:** TCP SYN scan (default Nmap behavior when not specifying service version or -sT/-sU explicitly).  
**Nmap version:** 7.95  
**Scan timestamp (from output):** 2025-09-22 08:33 EDT

---

## Files
- `scan_results.txt` — raw Nmap output (as produced by the user).
- `README.md` — this file, explanation, findings, mitigations, and interview answers.

---

## Commands used
Run from a terminal:
```bash
# Example used by student
nmap 192.168.1.0/24
# (Alternative more detailed scan examples)
nmap -sS 192.168.1.0/24        # SYN scan
nmap -sS -p 1-65535 192.168.1.0/24  # full TCP port range (slower)
nmap -sU -p 1-1024 192.168.1.0/24   # UDP scan (requires sudo/root)
nmap -sS -A 192.168.1.0/24    # aggressive scan (service detection, OS detect)
---

## Wireshark Analysis

In addition to Nmap scanning, I captured network traffic using **Wireshark** and saved it in  
`Wireshark_result.pcapng`.

### Purpose
- To observe packets generated during the Nmap scan.
- To understand how SYN, SYN-ACK, and RST packets confirm port states.

### Key Observations
- For **open ports (53/tcp on 192.168.44.2)**:
  - Wireshark shows **SYN → SYN-ACK → RST** sequence, meaning the port is open but connection was reset (since Nmap didn’t complete the handshake).
- For **closed ports**:
  - Wireshark shows **SYN → RST** response, meaning no service is listening.
- For **filtered ports**:
  - Wireshark shows no reply at all (packets dropped by firewall).

### Security Insights
- Wireshark provides packet-level confirmation of what Nmap detects.
- Useful for validating scans and learning how firewalls or services respond differently.
- Helps defenders investigate whether unexpected traffic or responses are occurring.

---

