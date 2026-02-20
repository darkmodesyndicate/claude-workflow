---
name: git-workflow
description: Git commit conventions, branch naming, PR standards, and commit message format. Invoke when committing, creating PRs, or reviewing git history.
---

# Git Workflow Conventions

## Commit Message Format (Conventional Commits)

All commits must follow Conventional Commits format:

```
<type>: <short description (50 chars max)>

<detailed explanation (wrap at 72 chars)>
- Bullet points for multiple changes
- Be specific about what changed and why
```

### Types

| Type | Use for |
|---|---|
| `feat:` | New feature |
| `fix:` | Bug fix |
| `refactor:` | Code restructuring without functional change |
| `docs:` | Documentation changes |
| `test:` | Adding or updating tests |
| `chore:` | Dependency updates, build config, tooling |
| `style:` | Code formatting, whitespace (no logic change) |
| `perf:` | Performance improvements |

### Example

```
feat: add candidate export to CSV

Implement CSV export for the candidate list view. Export respects
the currently applied search filters and column visibility settings.

Changes:
- Add ExportCandidatesJob for background processing
- Add CandidateExportService with column mapping logic
- Add download endpoint with signed URL delivery
- Queue job on the exports queue for isolation
```

## Rules

**No AI attribution** - do not include any of the following in commits, PRs, or issues:
- "Generated with Claude Code"
- "Co-Authored-By: Claude"
- "🤖 Generated with..."
- Any AI assistant signature or watermark

Commit messages must read as standard human-written commits.

**No emojis** in commit messages, PR titles, or issue titles.

## Branch Naming

```
<type>/<ticket-id>_<short-description>
```

Examples:
```
feat/CU-86af3rb23_add-candidate-export
fix/CU-91bx2kc11_fix-npi-validation
refactor/CU-77cc4dm44_extract-matching-service
chore/update-dependencies-feb-2026
```

- Use kebab-case for the description part
- Include the ClickUp ticket ID when one exists
- Keep it short enough to read in a terminal

## Commit Discipline

- Commit at logical checkpoints, not after every file edit
- Each commit should represent one coherent change
- Avoid "WIP" commits on shared branches; use stash or draft PRs instead
- Write migrations and their code changes in the same commit

## Pull Request Standards

### Title
Same format as a commit message subject line:
```
feat: add candidate export to CSV
```

### Body
```markdown
## Summary
- What changed and why (3 bullets max)

## Test plan
- [ ] Manually tested export on staging with filters applied
- [ ] Unit tests pass for CandidateExportService
- [ ] No regressions in candidate list view
```

No AI attribution in PR bodies.

## Workflow

```bash
# Stage all changes
git add -A

# Commit with message (use heredoc for multi-line)
git commit -m "$(cat <<'EOF'
feat: add candidate export to CSV

Implement CSV export with filter support and background processing.
EOF
)"

# Push branch and set upstream
git push -u origin feat/CU-86af3rb23_add-candidate-export
```

## What NOT to Do

- Never force-push to `main` or `master`
- Never amend commits that have been pushed to shared branches
- Never commit `.env` files, secrets, or credentials
- Never commit generated files (compiled assets, vendor/, node_modules/)
