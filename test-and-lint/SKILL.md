---
name: test-and-lint
description: Run tests and lint, fix any issues found. Use when the user wants to check code quality or fix lint/test failures.
---

# /test-and-lint — Run tests and lint, fix issues

Run the full test and lint suite and fix any problems found.

## Steps

1. **Run tests**: Execute the project's test command. Capture output.
   - If all tests pass, report the count and move on.
   - If any tests fail, analyze the failures, fix the code, and re-run until green.
2. **Run linter**: Execute the project's lint command.
   - If clean, report success.
   - If issues found, auto-fix what's possible, then manually fix the rest.
3. **Run formatter**: Check if files need formatting.
   - If files need formatting, run the formatter and report what changed.
4. **Summary**: Report final status — all green, or list remaining issues that need manual attention.

## Rules
- Never skip failing tests — investigate and fix them.
- If a test failure is caused by a genuine bug (not a test issue), fix the bug, not the test.
- Report clearly: how many tests passed, any lint issues fixed, any files reformatted.
