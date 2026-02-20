# Start Coding Session

I'll orient you for this session by reading accumulated project context and surfacing what's relevant to your current work.

## Steps

1. **Read `AI_CONTEXT.md`** in the current project directory (if it exists)
   - Surface any architecture decisions relevant to today's work
   - Note any known gotchas that apply
   - Highlight any open questions that may need resolution

2. **Check git state**
   - Current branch and what it indicates about the feature being worked on
   - Any uncommitted changes from a previous session

3. **Ask what we're working on today** (if not provided as arguments: `$ARGUMENTS`)

4. **Suggest relevant skills to invoke** based on the work described and available skills in your environment

5. **Confirm session scope** - summarize what we're doing and any relevant context from `AI_CONTEXT.md`

## Notes

- `AI_CONTEXT.md` is the accumulated memory for this project. It is tool-agnostic and readable by any AI assistant.
- If `AI_CONTEXT.md` does not exist, note this and suggest running `/session-end` at the end of the first session to create it.
- Do NOT write to `CLAUDE.md` during session start - that is a pointer file only.

**Important**: I will NEVER:
- Add "Co-authored-by" or any Claude signatures
- Include "Generated with Claude Code" or similar messages
- Modify git config or user credentials
- Add any AI/assistant attribution to commits or files
