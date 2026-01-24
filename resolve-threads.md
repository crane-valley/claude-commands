---
argument-hint: <pr-number>
description: Resolve all comment threads on a PR
---

Resolve all comment threads on PR #$ARGUMENTS:

1. Get all review threads via `gh api graphql`
2. For each unresolved thread, resolve it using `gh api graphql` mutation
3. Report how many threads were resolved

## GitHub API Reference

### Get all review threads with node IDs
```bash
gh api graphql -f query='
  query {
    repository(owner: "{owner}", name: "{repo}") {
      pullRequest(number: {pr}) {
        reviewThreads(first: 100) {
          nodes {
            id
            isResolved
            comments(first: 1) {
              nodes { body path line }
            }
          }
        }
      }
    }
  }'
```

### Resolve a single thread
```bash
gh api graphql -f query='
  mutation {
    resolveReviewThread(input: {threadId: "THREAD_NODE_ID"}) {
      thread { isResolved }
    }
  }'
```

Note: Replace {owner}, {repo}, {pr} with actual values. Get thread node IDs from the query above, then resolve each unresolved thread.
