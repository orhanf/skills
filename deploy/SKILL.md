---
name: deploy
description: Deploy to Railway and verify the deployment is healthy. Use when the user wants to deploy.
---

# /deploy — Deploy to Railway and verify

Deploy the current code to Railway and confirm it's running.

## Steps

1. **Pre-check**: Run `git status` to confirm there are no uncommitted changes. If there are, warn the user and stop — deploy should only ship committed code.
2. **Deploy**: Run `railway up` to trigger a deployment.
3. **Verify**: Wait a few seconds, then run `railway logs --deployment` (tail ~50 lines) to confirm:
   - The container started successfully
   - Migrations ran without errors
   - The application server is listening on the expected port
4. **Report**: Summarize the deploy status (success/failure) and include the Railway dashboard link from the deploy output.

## Rules

- Never deploy with uncommitted changes without explicit user approval.
- If the deploy fails, show the relevant error logs and suggest a fix.
- If migrations fail, do NOT retry automatically — report the error.
