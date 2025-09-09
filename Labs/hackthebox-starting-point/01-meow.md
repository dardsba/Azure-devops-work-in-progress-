---
title: "Lab: Meow"
status: "Completed"
track: "HTB Starting Point"
date: "2025-09-01"
---

# Lab: Meow

## Objective
Telnet (port 23) with root/no password.

## Methodology
1. **Recon** — Identify service/entry point.
2. **Finding** — Confirm misconfiguration/vulnerability.
3. **Exploit** — Execute the minimal steps to gain access.
4. **Post** — Retrieve proof, note hardening steps.

## Key Commands
```bash
nmap -sV -p 23 <host>
telnet <host>
# username: root, password: <empty>
```

## Lessons Learned
- Disable/lock down default or legacy services.
- Restrict network exposure; prefer MFA and least privilege.
- Monitor and alert on anomalous access.