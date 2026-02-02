---
description: Clean up local branch after PR merge
argument_description: "[PR number] - optional PR number to identify the branch"
---

PR merged and remote branch deleted. Clean up local:

## Arguments
- `$ARGUMENTS` may contain a PR number (e.g., "123")

## Steps
1. Identify the branch to clean up:
   - If PR number is provided in `$ARGUMENTS`: use `gh pr view <PR_NUMBER> --json headRefName` to get the branch name
   - If no argument: use current branch name
2. Check if this is a git worktree (`.git` is a file, not a directory):
   - **If worktree**: Find the bare repo via `git rev-parse --git-common-dir`, then:
     1. `git worktree remove <current-worktree-path>` (removes directory + worktree registration)
     2. Delete the branch in the bare repo: `git -C <bare-repo> branch -d <branch>`
     3. Fetch latest in bare repo: `git -C <bare-repo> fetch origin`
   - **If regular repo**:
     1. Checkout default branch (main/master)
     2. Pull latest
     3. Delete the branch locally (use -d first, -D if needed)
