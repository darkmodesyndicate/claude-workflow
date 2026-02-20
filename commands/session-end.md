# End Coding Session

I'll summarize this session and write accumulated knowledge to `AI_CONTEXT.md` so the next session (in any AI tool) starts with context.

## Steps

1. **Analyze what was accomplished**
   - Review files created or modified during the session
   - Check git log for commits made
   - Summarize completed work

2. **Identify what should be persisted**

   For each of these categories, determine if anything new was learned:

   - **Architecture decisions**: Any new decisions made and why? (e.g. "decided to use X pattern for Y reason")
   - **Known gotchas**: Anything discovered that is not obvious from reading the code?
   - **Established patterns**: New patterns that emerged that are not yet in `AI.md`?
   - **Open questions**: Unresolved decisions that need attention next session?

3. **Update `AI_CONTEXT.md`**

   Read the existing `AI_CONTEXT.md` file, then append new entries to the appropriate sections:

   - Add rows to the **Architecture Decisions** table for any decisions made
   - Add bullets to **Known Gotchas** for anything discovered
   - Add bullets to **Established Patterns** for new patterns
   - Add checkboxes to **Open Questions** for unresolved items
   - Mark resolved open questions with `[x]` if any were addressed

   Write the updated file back. Preserve all existing content - only append, do not remove previous entries.

4. **Session summary**

   Output a brief summary:
   - What was accomplished
   - What was written to `AI_CONTEXT.md`
   - Recommended next steps or branch to pick up

## Notes

- `AI_CONTEXT.md` is the tool-agnostic memory layer. It must be updated here, not in `CLAUDE.md`.
- If `AI_CONTEXT.md` does not exist in the project root, create it with the standard structure before writing.
- Only write genuinely useful context - skip boilerplate, obvious things, or things already in `AI.md`.

## Standard `AI_CONTEXT.md` Structure (if creating fresh)

```markdown
# Project Context

> Living document. Updated at the end of each coding session via `/session-end`.
> See `AI.md` for stable conventions and project setup.
> This file is tool-agnostic and readable by any AI assistant.

---

## Architecture Decisions

| Date | Decision | Rationale |
|------|----------|-----------|

---

## Known Gotchas

---

## Established Patterns

---

## Open Questions
```

**Important**: I will NEVER:
- Add "Co-authored-by" or any Claude signatures
- Include "Generated with Claude Code" or similar messages
- Modify git config or user credentials
- Add any AI/assistant attribution to commits or files
- Use emojis in commits, PRs, or git-related content
