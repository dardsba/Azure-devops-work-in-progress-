---
title: "Lab: Sequel"
status: "Completed"
track: "HTB Starting Point"
date: "2025-09-01"
---

# Lab: Sequel

## Objective
MariaDB/MySQL open root; enumerate DB schema (3306/tcp).

## Methodology
1. **Recon** — Identify service/entry point.
2. **Finding** — Confirm misconfiguration/vulnerability.
3. **Exploit** — Execute the minimal steps to gain access.
4. **Post** — Retrieve proof, note hardening steps.

## Key Commands
```bash
nmap -sV -p 3306 <host>
mysql -h <host> -u root
SHOW DATABASES; USE htb; SHOW TABLES; SELECT * FROM config;
```

## Lessons Learned
- Disable/lock down default or legacy services.
- Restrict network exposure; prefer MFA and least privilege.
- Monitor and alert on anomalous access.