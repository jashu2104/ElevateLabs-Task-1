# Task 1 — Local Network Port Scan (Nmap)

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
