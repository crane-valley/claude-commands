---
argument-hint: <pr-number>
description: Resolve all comment threads on a PR
---

Resolve all comment threads on PR #$ARGUMENTS:

1. Get all review threads via `gh api graphql`
2. For each unresolved thread, resolve it using `gh api graphql` mutation
3. Report how many threads were resolved
