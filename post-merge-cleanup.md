---
description: Clean up local branch after PR merge
argument_description: "[PR number] - optional PR number to identify the branch"
---

PR merged and remote branch deleted. Clean up local:

## Arguments
- `$ARGUMENTS` may contain a PR number (e.g., "123")

## Steps
1. Identify the branch to delete:
   - If PR number is provided in `$ARGUMENTS`: use `gh pr view <PR_NUMBER> --json headRefName` to get the branch name
   - If no argument: use current branch name
2. Checkout default branch (main/master)
3. Pull latest
4. Delete the identified branch locally (use -d first, -D if needed)
