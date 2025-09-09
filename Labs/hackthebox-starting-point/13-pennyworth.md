---
title: "Lab: Pennyworth"
status: "Completed"
track: "HTB Starting Point"
date: "2025-09-01"
---

# Lab: Pennyworth

## Objective
Jenkins Script Console RCE with weak creds.

## Methodology
1. **Recon** — Identify service/entry point.
2. **Finding** — Confirm misconfiguration/vulnerability.
3. **Exploit** — Execute the minimal steps to gain access.
4. **Post** — Retrieve proof, note hardening steps.

## Key Commands
```bash
browse http://<host>:8080
# login with weak creds
# Manage Jenkins → Script Console (Groovy reverse shell)
```

## Lessons Learned
- Disable/lock down default or legacy services.
- Restrict network exposure; prefer MFA and least privilege.
- Monitor and alert on anomalous access.