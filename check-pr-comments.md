---
argument-hint: <pr-number>
description: Review PR comments, fix issues, reply and resolve
---

Review comments on PR #$ARGUMENTS. Fix issues if needed, reply to each comment, and resolve them.

## Workflow
1. Get PR comments: `gh api repos/{owner}/{repo}/pulls/{pr}/comments`
2. Get review threads: `gh pr view {pr} --comments` or use GraphQL
3. Fix any issues mentioned in comments
4. Reply to each comment (see API below)
5. Resolve each thread (see API below)

## GitHub API Reference

### Reply to a review comment
```bash
gh api repos/{owner}/{repo}/pulls/{pr}/comments/{comment_id}/replies \
  -f body="Reply message here"
```

### Resolve a review thread (GraphQL)
```bash
gh api graphql -f query='
  mutation {
    resolveReviewThread(input: {threadId: "THREAD_NODE_ID"}) {
      thread { isResolved }
    }
  }'
```

### Get thread node IDs
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
              nodes { body }
            }
          }
        }
      }
    }
  }'
```
