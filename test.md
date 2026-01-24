---
argument-hint: [test-pattern]
description: Run tests
---

Run tests for this project:

1. Detect the project type and test framework:
   - Node.js: npm test or npx jest/vitest
   - Python: pytest or python -m unittest
   - Rust: cargo test
   - .NET: dotnet test
2. If $ARGUMENTS is provided, use it as a test filter/pattern
3. Run the tests and report results
