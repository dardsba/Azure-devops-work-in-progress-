---
title: "Lab: Ignition"
status: "Completed"
track: "HTB Starting Point"
date: "2025-09-01"
---

# Lab: Ignition

## Objective
Magento admin via default/weak creds.

## Methodology
1. **Recon** — Identify service/entry point.
2. **Finding** — Confirm misconfiguration/vulnerability.
3. **Exploit** — Execute the minimal steps to gain access.
4. **Post** — Retrieve proof, note hardening steps.

## Key Commands
```bash
ffuf/gobuster to find /admin
# try default/admin creds
```

## Lessons Learned
- Disable/lock down default or legacy services.
- Restrict network exposure; prefer MFA and least privilege.
- Monitor and alert on anomalous access.