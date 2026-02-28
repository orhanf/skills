# /ship — Test, lint, commit, and push

Run the full pre-deploy quality cycle and ship the current changes.

## Steps

1. **Run tests**: Execute the project's test command (e.g., `pytest`, `npm test`). If any fail, fix the issues before proceeding.
2. **Run linter**: Execute the project's lint command (e.g., `ruff check`, `eslint`). Fix any lint errors found.
3. **Run formatter**: Execute the project's format command if configured. Check if formatting produced changes.
4. **Commit**: Stage all modified/new files relevant to the current work (never stage `.env`, credentials, or unrelated files). Write a clear commit message following the repo's convention.
5. **Push**: Push to the current branch's remote.

## Rules

- Stop and report if tests or lint fail and you cannot auto-fix.
- Never force-push. Never push to main/master without confirmation.
- Only commit files related to the current task — review `git status` first.
- If there are no changes to commit, say so and stop.

## Usage

```
/ship
/ship just the view and template changes
```
