---
argument-hint: <folder-path>
description: Switch working directory and do a quick repo check
---

Work in: $ARGUMENTS

Quick repo check:

1. **Detect repo type**:
   - Check if `.bare` directory exists (bare worktree setup)
   - Check if `.git` is a file (inside a worktree) or directory (regular repo)

2. **If bare worktree setup** (`.bare/` exists):
   - Run `git worktree list` to show all worktrees and their branches
   - Pull latest in the main worktree: `git -C <path>/main pull`
   - Show project structure from the main worktree
   - Read README.md and CLAUDE.md from the main worktree if they exist

3. **If inside a specific worktree** (`.git` is a file):
   - Show which branch this worktree tracks
   - Run `git worktree list` to show sibling worktrees
   - Pull latest for this worktree
   - Show project structure
   - Read README.md and CLAUDE.md if they exist

4. **If regular repo** (`.git` is a directory):
   - Checkout default branch (main/master) and pull latest
   - Show project structure (list main dirs)
   - Read README.md and CLAUDE.md if they exist

5. Identify tech stack

Brief summary please.
