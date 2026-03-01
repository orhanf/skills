# Claude Code Skills

Reusable [Claude Code](https://claude.ai/code) slash-command skills that can be dropped into any project's `.claude/skills/` directory.

## Skills

| Skill | Directory | Description |
|-------|-----------|-------------|
| `/ship` | [ship/](ship/) | Test, lint, commit, and push in one command |
| `/deploy` | [deploy/](deploy/) | Deploy to Railway and verify logs |
| `/check-deploy` | [check-deploy/](check-deploy/) | Check Railway deployment health |
| `/django-feature` | [django-feature/](django-feature/) | Scaffold a complete Django feature end-to-end |
| `/test-and-lint` | [test-and-lint/](test-and-lint/) | Run tests + lint and fix any issues |
| `/serverless_cron_scraper` | [serverless_cron_scraper.md](serverless_cron_scraper.md) | Set up a serverless cron scraper using GitHub Actions |

## Usage

### Per-project (recommended)
Copy the skill directories you need into your project:
```bash
mkdir -p .claude/skills
cp -r ~/skills/ship .claude/skills/
```

### Global (available in all projects)
```bash
cp -r ~/skills/ship ~/.claude/skills/
```

Then invoke with `/ship`, `/deploy`, etc. inside Claude Code.

## Structure

Each skill follows the Claude Code skill format:
```
<skill-name>/
  SKILL.md    # Skill instructions with YAML frontmatter (name, description)
```

## Customization

These skills are written to be general-purpose. Adapt them to your project:
- **Test/lint commands**: Update `pytest`, `ruff` to match your tooling (e.g., `jest`, `eslint`).
- **Deploy target**: `deploy.md` assumes Railway — swap for Fly.io, Vercel, etc.
- **Django conventions**: `django-feature` follows a specific Django pattern — adjust to your project structure.
