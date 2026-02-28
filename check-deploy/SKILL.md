---
name: check-deploy
description: Check Railway deployment status and logs. Use when the user wants to check if the deploy is healthy.
---

# /check-deploy — Check Railway deployment status and logs

Quickly check whether the current Railway deployment is healthy.

## Steps

1. Run `railway logs --deployment` and show the last 50 lines.
2. Look for:
   - **Healthy indicators**: Application server started, listening on port, migrations applied successfully.
   - **Error indicators**: Tracebacks, "Error", "FATAL", migration failures, import errors, connection refused.
3. Summarize the status: healthy, degraded, or failed.
4. If errors are found, suggest concrete next steps to fix them.
