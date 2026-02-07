---
argument-hint: <feature-description>
description: Parallel feature development with agent team (architect + builders)
---

Create an agent team to implement: $ARGUMENTS

Follow this phased approach:

## Phase 0: Worktree Setup

1. **Detect if we're in a bare worktree repo** (`.bare/` exists or `.git` is a file):
   - If yes, create a dedicated worktree for this feature before starting:
     - Branch name based on task (e.g., `feature/add-auth`)
     - `git worktree add "<repo-root>/feature/xxx" -b "feature/xxx"`
   - If builder teammates need isolated workspaces, create additional worktrees branched from the feature branch
   - If not a worktree repo, proceed normally

## Phase 1: Architecture (sequential)

2. **Spawn an architect teammate** (use Opus, require plan approval):
   - "Design the architecture for: $ARGUMENTS. Analyze the existing codebase structure, identify where new code should live, define interfaces/contracts between components, and create a detailed implementation plan. Do NOT write implementation code - only interfaces, types, and the plan."

3. **Review and approve** the architect's plan
   - Ensure clear file ownership boundaries (no two builders should touch the same file)
   - Verify interfaces are well-defined
   - Check that tasks are properly scoped

## Phase 2: Implementation (parallel)

4. **Spawn builder teammates** (use Sonnet) based on the architect's plan:
   - One per independent module/layer (e.g., frontend, backend, database, tests)
   - **Worktree repos**: each builder works in the feature worktree. If builders might conflict on files, create separate worktrees per builder and merge later.
   - Each builder gets:
     - The approved architecture plan
     - Their specific assigned files and tasks
     - The interfaces they must implement
     - Explicit instruction: "Only modify files assigned to you"

5. **Coordinate builders**:
   - Use delegate mode - do NOT implement yourself
   - Assign 5-6 tasks per builder from the task list
   - Set dependencies (e.g., DB layer before service layer)
   - If a builder finishes early, assign remaining unblocked tasks

## Phase 3: Integration (sequential)

6. **Spawn an integration teammate** (use Sonnet) after all builders finish:
   - "Verify all components integrate correctly. Run tests, check imports, ensure interfaces match implementations. Fix any integration issues."

7. **Wrap up**:
   - Shut down all teammates
   - Clean up the team
   - Summarize: what was built, files changed, any remaining TODOs
   - Update PLANS.md if it exists
