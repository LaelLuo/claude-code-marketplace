---
description: Monitor user input for OpenSpec workflow keywords and provide appropriate guidance
---

**Context:** User has submitted a prompt. Check if OpenSpec workflow guidance is needed.

**Step 1: Check if OpenSpec project**
First, verify this is an OpenSpec project by checking if `openspec/project.md` exists.
- If NOT an OpenSpec project: Do nothing, proceed normally
- If IS an OpenSpec project: Continue to Step 2

**Step 2: Analyze user intent**
Check if the user's request matches these patterns:

**Requires OpenSpec proposal (remind user):**
- Adding new features or capabilities
  - Keywords: "add feature", "new feature", "implement feature", "create feature"
- Making breaking changes
  - Keywords: "breaking change", "breaking", "change API", "change schema"
- Architectural changes
  - Keywords: "architecture", "refactor architecture", "redesign", "restructure"
- Performance changes that alter behavior
  - Keywords: "optimize", "improve performance" (if changes behavior)
- Security pattern updates
  - Keywords: "security", "authentication", "authorization" (if new or changed)
- Explicitly mentions proposals/specs
  - Keywords: "proposal", "spec", "change proposal", "create spec"

**Does NOT require proposal (allow direct fix):**
- Bug fixes restoring intended behavior
  - Keywords: "fix bug", "bug fix", "restore", "repair"
- Typos, formatting, comments
  - Keywords: "typo", "format", "comment", "documentation"
- Non-breaking dependency updates
  - Keywords: "update dependency", "upgrade package" (if non-breaking)
- Configuration changes
  - Keywords: "config", "configuration", "settings" (if not architectural)
- Tests for existing behavior
  - Keywords: "add test", "write test" (for existing features)

**Step 3: Provide guidance**
If the request requires a proposal:
```
⚠️ This looks like a change that should follow the OpenSpec workflow.

Before implementing, consider creating a change proposal:
1. Run: openspec list (check existing work)
2. Create proposal: openspec/changes/<change-id>/
3. Validate: openspec validate <change-id> --strict

Would you like me to create an OpenSpec proposal for this change?
```

If the request is a direct fix:
```
✓ This looks like a direct fix. Proceeding without OpenSpec proposal.
```

**Step 4: Respect user choice**
- If user says "yes" to proposal: Create proposal following OpenSpec workflow
- If user says "no" or "just fix it": Proceed with direct implementation
- If user is unsure: Explain benefits of proposal (alignment, review, documentation)

**Important notes:**
- Be helpful, not blocking
- Respect user's decision
- Keep guidance concise
- Don't repeat if user already mentioned "proposal" or "spec"
- If ambiguous, err on side of suggesting proposal (safer)

**Example scenarios:**

User: "Add two-factor authentication"
→ Requires proposal (new feature)
→ Show guidance

User: "Fix the login bug where password validation fails"
→ Direct fix (bug fix)
→ Proceed without proposal

User: "Update the authentication to use OAuth instead of JWT"
→ Requires proposal (breaking change, architecture)
→ Show guidance

User: "Fix typo in README"
→ Direct fix (typo)
→ Proceed without proposal

User: "I want to create a proposal for adding search filters"
→ User already knows to use OpenSpec
→ Don't show guidance, just help create proposal

User: "Refactor the database layer to use Prisma"
→ Requires proposal (architecture change)
→ Show guidance
