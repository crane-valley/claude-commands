---
argument-hint: <task-description>
description: Start an agent team with auto-structured roles for a given task
---

Create an agent team to work on: $ARGUMENTS

Follow these steps:

1. **Analyze the task** and determine the optimal team structure:
   - Identify 2-4 independent work streams that can run in parallel
   - Each teammate should own a distinct set of files to avoid conflicts
   - Size tasks so each produces a clear deliverable (a function, test file, module, etc.)

2. **Worktree setup** (if in a bare worktree repo):
   - Check if `.bare/` exists or `.git` is a file
   - If yes, create a worktree for the task branch: `git worktree add "<repo-root>/<branch>" -b "<branch>"`
   - If teammates need fully isolated workspaces, create per-teammate worktrees
   - All teammates should be told their working directory path

3. **Create the team** with these guidelines:
   - Give each teammate a descriptive name reflecting their role
   - Use Sonnet for implementation teammates, Opus for architecture/review teammates
   - Require plan approval for teammates making architectural changes
   - Include full context in each teammate's spawn prompt (file paths, conventions, constraints)

4. **Set up the task list** with:
   - 5-6 tasks per teammate for steady progress
   - Clear dependencies between tasks (e.g., interfaces before implementations)
   - Acceptance criteria for each task

5. **Coordinate the work**:
   - Use delegate mode (Shift+Tab) - do NOT implement tasks yourself
   - Wait for teammates to finish before synthesizing results
   - Monitor progress and redirect teammates if they get stuck
   - If a teammate finishes early, assign remaining unblocked tasks

6. **Wrap up**:
   - Verify all tasks are completed
   - Shut down all teammates gracefully
   - Clean up the team
   - Summarize what was accomplished

Important rules:
- Never let two teammates edit the same file (use separate worktrees if needed)
- Give each teammate enough context (they don't inherit your conversation history)
- If a task is too small for a team, say so and handle it in a single session instead
