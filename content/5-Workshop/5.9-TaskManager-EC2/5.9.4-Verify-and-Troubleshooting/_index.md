---
title: "Verify & troubleshooting"
date: 2026-09-01
weight: 4
chapter: false
pre: " <b>5.9.4.</b> "
---

## Expected outcome

- Backend running as a systemd service and auto-starting on reboot
- `POST /api/auth/register` returns a JWT token
- `GET /actuator/health` returns `{"status":"UP"}` when checked with `curl`

![POST /api/auth/register returning JWT](/images/5-Workshop/5.9-TaskManager-EC2/06-register-jwt.png)

*`POST /api/auth/register` returns a JWT token.*

## Troubleshooting

| Issue | Fix |
|-------|-----|
| EC2 cannot connect to RDS | Check the RDS Security Group inbound rule for port 3306 — source must be the EC2 Security Group, not public |
| Login returns `403` and the log shows `SignatureException: JWT signature does not match` | `JWT_SECRET` in `app.env` is too short (< 32 characters). Use a string of at least 32 characters and restart the service |
| Backend runs but with wrong config (issued tokens are rejected) | The properties are read under the `app.*` prefix (e.g. `@Value("${app.jwt.secret}")`). When running `java -jar`, pass `--app.jwt.secret`, `--app.aws.region`, `--app.ai.enabled` — not `--jwt.secret`, `--aws.region`, `--ai.enabled` |
| App fails to start with `Unknown database 'taskmanager'` | The database was not created on RDS — see the Troubleshooting in [5.8.3](../5.8-TaskManager-RDS/5.8.3-Verify-and-Troubleshooting) |