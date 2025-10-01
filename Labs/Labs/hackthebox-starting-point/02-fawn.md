---
title: "Lab: Fawn"
status: "Completed"
track: "HTB Starting Point"
date: "2025-09-01"
---

# Lab: Fawn

## Objective
FTP anonymous login (21/tcp).

## Methodology
1. **Recon** — Identify service/entry point.
2. **Finding** — Confirm misconfiguration/vulnerability.
3. **Exploit** — Execute the minimal steps to gain access.
4. **Post** — Retrieve proof, note hardening steps.

## Key Commands
```bash
nmap -sV -p 21 <host>
ftp <host>
# user: anonymous, pass: <empty>
ftp> ls
ftp> get flag.txt
```

## Lessons Learned
- Disable/lock down default or legacy services.
- Restrict network exposure; prefer MFA and least privilege.
- Monitor and alert on anomalous access.