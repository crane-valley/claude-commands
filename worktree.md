---
argument-hint: <branch-name>
description: Create a new git worktree for a branch (e.g., feature/add-auth)
---

Create a new worktree for branch: $ARGUMENTS

## Steps

1. **Verify we're in a bare worktree repo**:
   - Check if `.bare/` exists in the repo root, or find it via `git rev-parse --git-common-dir`
   - If not a bare worktree setup, explain and abort

2. **Determine the repo root**:
   - If currently inside a worktree, find the parent bare repo root
   - The repo root is the directory containing `.bare/` and `main/`

3. **Create the worktree**:
   - Target path: `<repo-root>/$ARGUMENTS` (e.g., `E:\wktr\kylix\feature\add-auth`)
   - Ensure parent directories exist
   - Run: `git worktree add "<repo-root>/$ARGUMENTS" -b "$ARGUMENTS"`
   - If the branch already exists remotely, track it: `git worktree add "<repo-root>/$ARGUMENTS" "$ARGUMENTS"`

4. **Verify and report**:
   - Run `git worktree list` to confirm
   - Show the full path to the new worktree
   - Suggest: "Run `/work-in <path>` to start working there"
