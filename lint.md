---
argument-hint: [path]
description: Run linter and formatter
---

Run linter/formatter for this project:

1. Detect the project type and linter:
   - Node.js: npm run lint or npx eslint
   - Python: ruff check or flake8
   - Rust: cargo clippy && cargo fmt --check
   - .NET: dotnet format --verify-no-changes
2. If $ARGUMENTS is provided, lint only that path
3. Report any issues found
