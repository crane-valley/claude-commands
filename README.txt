# Claude Code Custom Commands

Custom slash commands for Claude Code CLI.

## Commands

### /work-in <folder-path>
Switch working directory and get a quick overview of the repository.
- Lists project structure
- Reads README.md and CLAUDE.md if present
- Identifies tech stack

### /check-pr-comments <pr-number>
Review comments on a GitHub PR.
- Fixes issues if needed
- Replies to each comment
- Resolves addressed comments

## Installation

Copy .md files to your Claude Code commands directory:
- Windows: %USERPROFILE%\.claude\commands\
- macOS/Linux: ~/.claude/commands/

Or clone directly:
  git clone https://github.com/crane-valley/claude-commands.git ~/.claude/commands

## Why README.txt instead of README.md?

Claude Code recognizes all .md files in the commands directory as slash commands.
Using .txt avoids /README appearing in the command list.

## License

MIT License - See LICENSE file
