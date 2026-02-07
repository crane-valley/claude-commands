---
argument-hint: <pr-number>
description: Parallel PR review with agent team (security, performance, tests)
---

Create an agent team to thoroughly review PR #$ARGUMENTS from multiple angles.

1. **Get PR context first**:
   - Run `gh pr view $ARGUMENTS` for PR description
   - Run `gh pr diff $ARGUMENTS` to understand the scope of changes
   - Identify the changed files and affected modules

2. **Spawn 3 review teammates** (use Sonnet for all):

   **security-reviewer**: "Review PR #$ARGUMENTS focusing exclusively on security. Check for:
   - Injection vulnerabilities (SQL, XSS, command injection)
   - Authentication/authorization issues
   - Secrets or credentials in code
   - Input validation gaps
   - OWASP Top 10 concerns
   Rate each finding as critical/high/medium/low severity."

   **perf-reviewer**: "Review PR #$ARGUMENTS focusing exclusively on performance. Check for:
   - N+1 queries or unnecessary DB calls
   - Missing indexes for new queries
   - Memory leaks or unbounded growth
   - Expensive operations in hot paths
   - Missing caching opportunities
   - Bundle size impact (if frontend)
   Quantify impact where possible."

   **quality-reviewer**: "Review PR #$ARGUMENTS focusing exclusively on code quality and correctness. Check for:
   - Logic errors and edge cases
   - Missing or inadequate test coverage
   - Error handling gaps
   - API contract changes (breaking changes)
   - Code style and naming consistency
   - Dead code or unnecessary complexity
   Suggest specific improvements."

3. **Wait for all reviewers** to complete their analysis

4. **Synthesize findings** into a single review:
   - Group by severity (critical → low)
   - Remove duplicates across reviewers
   - Provide actionable fix suggestions for each issue
   - Give an overall assessment: approve / request changes / needs discussion

5. **Clean up the team** after synthesis is complete
