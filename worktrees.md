---
description: List all worktrees in the current bare repo
---

List all worktrees for this repository.

1. **Find the bare repo root**:
   - If `.bare/` exists here, use current directory
   - Otherwise, find it via `git rev-parse --git-common-dir` and navigate to its parent

2. **List worktrees**: run `git worktree list`

3. **For each worktree, show**:
   - Path
   - Branch name
   - Last commit (short hash + subject)
   - Status: clean / has uncommitted changes (`git -C <path> status --short`)

4. **Check for stale worktrees**: `git worktree prune --dry-run`
   - If any stale entries found, suggest running `git worktree prune`
