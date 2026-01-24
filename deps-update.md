---
description: Check for dependency updates
---

Check for outdated dependencies:

1. Detect the project type:
   - Node.js: npm outdated
   - Python: pip list --outdated
   - Rust: cargo outdated (if installed) or check Cargo.toml
   - .NET: dotnet list package --outdated
2. Report which packages have updates available
3. Highlight any security-related updates
