---
argument-hint: <pr-number>
description: Diagnose and fix failed PR checks
---

PR #$ARGUMENTS checks failed. Diagnose and fix:
1. Get failed check details via `gh pr checks $ARGUMENTS`
2. Identify failure cause (lint, test, build, etc.)
3. Fix the issues
4. Commit and push