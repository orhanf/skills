# Claude Code Skills

Reusable [Claude Code](https://claude.ai/code) slash-command skills that can be dropped into any project's `.claude/commands/` directory.

## Skills

| Skill | File | Description |
|-------|------|-------------|
| `/ship` | [ship.md](ship.md) | Test, lint, commit, and push in one command |
| `/deploy` | [deploy.md](deploy.md) | Deploy to Railway and verify logs |
| `/check-deploy` | [check-deploy.md](check-deploy.md) | Check Railway deployment health |
| `/django-feature` | [django-feature.md](django-feature.md) | Scaffold a complete Django feature end-to-end |
| `/test-and-lint` | [test-and-lint.md](test-and-lint.md) | Run tests + lint and fix any issues |

## Usage

### Per-project (recommended)
Copy the skills you need into your project:
```bash
mkdir -p .claude/commands
cp ~/skills/ship.md .claude/commands/
```

### Global (available in all projects)
```bash
cp ~/skills/ship.md ~/.claude/commands/
```

Then invoke with `/ship`, `/deploy`, etc. inside Claude Code.

## Customization

These skills are written to be general-purpose. Adapt them to your project:
- **Test/lint commands**: Update `pytest`, `ruff` to match your tooling (e.g., `jest`, `eslint`).
- **Deploy target**: `deploy.md` assumes Railway — swap for Fly.io, Vercel, etc.
- **Django conventions**: `django-feature.md` follows a specific Django pattern — adjust to your project structure.
