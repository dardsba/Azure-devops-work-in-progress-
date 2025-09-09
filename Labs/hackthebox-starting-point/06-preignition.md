---
title: "Lab: Preignition"
status: "Completed"
track: "HTB Starting Point"
date: "2025-09-01"
---

# Lab: Preignition

## Objective
Hidden admin panel; default credentials.

## Methodology
1. **Recon** — Identify service/entry point.
2. **Finding** — Confirm misconfiguration/vulnerability.
3. **Exploit** — Execute the minimal steps to gain access.
4. **Post** — Retrieve proof, note hardening steps.

## Key Commands
```bash
nmap -sV -p 80 <host>
gobuster dir -u http://<host>/ -w /usr/share/dirb/wordlists/common.txt
# visit /admin.php and try defaults (e.g., admin:admin)
```

## Lessons Learned
- Disable/lock down default or legacy services.
- Restrict network exposure; prefer MFA and least privilege.
- Monitor and alert on anomalous access.