---
title: "Lab: Crocodile"
status: "Completed"
track: "HTB Starting Point"
date: "2025-09-01"
---

# Lab: Crocodile

## Objective
Anonymous FTP leaks creds → web login.

## Methodology
1. **Recon** — Identify service/entry point.
2. **Finding** — Confirm misconfiguration/vulnerability.
3. **Exploit** — Execute the minimal steps to gain access.
4. **Post** — Retrieve proof, note hardening steps.

## Key Commands
```bash
ftp <host> (anonymous)
get users.txt
get passwords.txt
gobuster dir -u http://<host>/ -w /usr/share/dirb/wordlists/common.txt -x php
```

## Lessons Learned
- Disable/lock down default or legacy services.
- Restrict network exposure; prefer MFA and least privilege.
- Monitor and alert on anomalous access.