# Feature Planning

I'll help you think through a feature, explore the codebase, and produce a structured plan document ready for implementation.

Arguments: `$ARGUMENTS` - a feature name, description, or subcommand (`revise`, `status`)

---

## Subcommands

- `/plan [feature description]` — start a new planning session
- `/plan revise [feedback]` — iterate on the current draft without starting over
- `/plan status` — show the current draft plan if one exists in this session

---

## Phase 1: Context Check

**Before asking anything, check the conversation history.**

If the user has already been discussing this feature in the current conversation — describing requirements, raising concerns, mentioning constraints — treat that discussion as the starting context and skip or shorten the clarification questions accordingly. Do not ask questions that have already been answered.

If `$ARGUMENTS` is empty and there is no prior discussion, ask the user what feature they want to plan before proceeding.

---

## Phase 2: Clarification

Ask only the questions that are genuinely unanswered. Cover these areas, but skip any already clear from context:

1. **What is the feature?** — What does it do from the user's perspective? What problem does it solve?
2. **Who is affected?** — Which user types (Candidate, Recruiter, Admin, API consumer)?
3. **Scope boundaries** — What is explicitly out of scope for this iteration?
4. **Known constraints** — Any technical constraints, deadlines, or decisions already made?
5. **Reference material** — Any existing code, designs, or tickets to reference?

Keep this conversational. Two or three focused questions is better than a long form. Wait for answers before proceeding to codebase exploration.

---

## Phase 3: Codebase Exploration (Plan Subagent)

Once the feature is understood, launch a **Plan subagent** with the following task:

```
Explore the codebase to support planning for: [feature description]

Find and return:
1. Existing code that is directly relevant (models, services, controllers, Livewire components, migrations, routes)
2. Patterns already established in the codebase that this feature should follow
3. Potential conflicts or complications (naming, route collisions, event name clashes, existing similar functionality)
4. Suggested implementation layers — which existing structures to extend vs. create fresh
5. A proposed list of files to create and files to modify, with a brief reason for each
```

Review the subagent's findings before drafting the plan. If the findings reveal something that changes the scope or approach, surface it to the user before writing.

---

## Phase 4: Draft the Plan

Write the plan to `plans/YYYY-MM-DD_kebab-case-feature-name.md` using today's date.

Use this structure:

```markdown
# [Feature Name] - Implementation Plan

**Date:** YYYY-MM-DD
**Branch:** feat/[ticket-id]_kebab-case-name (or TBD if not yet created)
**Status:** Planning

---

## Overview

[2-4 sentence description of the feature, its purpose, and the approach.]

---

## Requirements

[Bulleted list of what this feature must do. Be specific. Each bullet should be independently verifiable.]

---

## Out of Scope

[What is explicitly not included in this iteration.]

---

## Implementation Plan

[Break the work into phases or logical groups. Each phase should have:]

### Phase N: [Name]

**Goal:** [One sentence.]

[Description of the work, key decisions, and approach.]

**Files to create:**
- `path/to/File.php` — [purpose]

**Files to modify:**
- `path/to/Existing.php` — [what changes]

**Implementation checklist:**
- [ ] Task one
- [ ] Task two

---

## Implementation Order

[Numbered list of phases/steps in the order they should be executed and why.]

---

## Technical Considerations

[Any non-obvious technical decisions, tradeoffs, or things to be aware of during implementation.]

---

## Rollback Plan

[How to undo this if something goes wrong — typically git revert + which migrations to reverse if any.]

---

## Open Questions

- [ ] [Any unresolved decisions that need an answer before or during implementation]

---

## Success Criteria

- [ ] [Verifiable statement of what "done" looks like]
- [ ] [Include test coverage expectation, manual test steps, or acceptance criteria]
```

**Calibrate the depth to the feature size.** A small bug fix or minor addition doesn't need a Rollback Plan section. A multi-phase feature with migrations does. Use judgment and omit sections that add no value for the specific feature.

---

## Phase 5: Present and Iterate

After writing the file:

1. Output a concise summary (not the full plan — the user can read the file):
   - What the feature does
   - How many phases / how much work
   - Key files affected
   - Any open questions or concerns surfaced during exploration

2. Ask: "Does this look right, or would you like to adjust anything?"

3. If the user requests changes, apply them to the plan file and confirm what was updated. Do not rewrite the whole plan unless asked — make targeted edits.

**For `/plan revise [feedback]`:**
- Read the existing plan file from this session
- Apply only the changes described in the feedback
- Confirm what changed

---

## Notes

- Plan files live in `plans/` in the project root
- File naming: `YYYY-MM-DD_kebab-case-description.md` — use today's date and a short descriptive name
- The plan file is the handoff to `/implement` — write it so that `/implement plans/your-plan.md` can pick it up directly
- Do not begin any implementation during planning — this command produces a document, not code
- If the exploration reveals the feature is significantly more complex than expected, say so clearly before writing the plan

**Important**: I will NEVER:
- Begin implementing code during the planning phase
- Add AI attribution or signatures to the plan document
- Use emojis in the plan document
