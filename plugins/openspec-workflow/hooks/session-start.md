---
description: Detect OpenSpec projects on session start and activate workflow guidance
---

You are starting a new session. Check if this is an OpenSpec project by looking for the `openspec/project.md` file.

**Detection steps:**
1. Check if `openspec/project.md` exists in the current working directory
2. If it exists, this is an OpenSpec project

**If OpenSpec project detected:**
Inform the user briefly:
```
📋 OpenSpec project detected. Spec-driven development workflow is active.
```

Then, internally note that you should:
- Follow OpenSpec three-stage workflow (Create → Implement → Archive)
- Create proposals before implementing features or breaking changes
- Use `openspec` CLI commands for validation and archiving
- Reference the openspec-workflow skill for detailed guidance

**If NOT an OpenSpec project:**
Do nothing. Proceed with normal session.

**Important:**
- Keep the notification brief (one line)
- Don't overwhelm the user with instructions
- The openspec-workflow skill will provide detailed guidance when needed
- Only activate if `openspec/project.md` exists (not just `openspec/` directory)
