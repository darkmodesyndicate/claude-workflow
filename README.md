# claude-workflow

Claude Code plugin providing development workflow commands for any project type.

## What's Included

### Commands (25)

| Command | Description |
|---------|-------------|
| `/workflow:plan` | Create structured implementation plans for features |
| `/workflow:implement` | Intelligently implement features from plans, URLs, or descriptions |
| `/workflow:review` | Review code for potential issues and improvements |
| `/workflow:commit` | Create well-formatted conventional commits |
| `/workflow:refactor` | Refactor code with clear before/after documentation |
| `/workflow:test` | Generate or update tests for your code |
| `/workflow:session-start` | Begin a coding session with project context |
| `/workflow:session-end` | End session and write accumulated knowledge to AI_CONTEXT.md |
| `/workflow:scaffold` | Generate boilerplate code and project structures |
| `/workflow:understand` | Deep-dive analysis of codebases or features |
| `/workflow:docs` | Generate or update documentation |
| `/workflow:security-scan` | Scan code for security vulnerabilities |
| `/workflow:predict-issues` | Predict potential problems before they occur |
| `/workflow:create-todos` | Create structured TODO lists from requirements |
| `/workflow:find-todos` | Find TODO comments in codebase |
| `/workflow:fix-todos` | Resolve TODO items systematically |
| `/workflow:todos-to-issues` | Convert TODOs to GitHub/GitLab issues |
| `/workflow:format` | Format code according to project standards |
| `/workflow:fix-imports` | Fix and organize import statements |
| `/workflow:remove-comments` | Remove unnecessary comments |
| `/workflow:make-it-pretty` | Improve code aesthetics and readability |
| `/workflow:cleanproject` | Clean up project files and dependencies |
| `/workflow:contributing` | Generate CONTRIBUTING.md for your project |
| `/workflow:explain-like-senior` | Get senior engineer-level explanations |
| `/workflow:undo` | Safely undo recent changes |

### Skills (2)

| Skill | Invoke | When to Use |
|-------|--------|-------------|
| **git-workflow** | `/workflow:git-workflow` | Conventional commits, branch naming, PR standards |
| **openapi-spec-generation** | `/workflow:openapi-spec-generation` | OpenAPI 3.1 specs, API documentation, SDK generation |

## Installation

```bash
# Add the plugin marketplace (if not already added)
/plugin marketplace add darkmodesyndicate/claude-workflow

# Install the plugin
/plugin install claude-workflow
```

## Usage

### Basic Workflow

Start your coding session with context:
```
/workflow:session-start
```

Plan a feature:
```
/workflow:plan Add user authentication with JWT tokens
```

Implement from the plan:
```
/workflow:implement
```

Review your changes:
```
/workflow:review
```

Commit with conventional format:
```
/workflow:commit
```

End your session and save context:
```
/workflow:session-end
```

### Advanced Examples

**Smart implementation from external sources:**
```
/workflow:implement https://github.com/example/feature.ts
```

**Generate tests for a specific file:**
```
/workflow:test src/services/auth.ts
```

**Security scan before deploying:**
```
/workflow:security-scan
```

**Understand complex code:**
```
/workflow:understand How does the authentication flow work?
```

## The Session Workflow

This plugin is designed around a complete development loop:

1. **`/workflow:session-start`** - Load project context from AI_CONTEXT.md
2. **`/workflow:plan`** - Think through features and create implementation plans
3. **`/workflow:implement`** - Execute the plan with intelligent code generation
4. **`/workflow:review`** - Catch issues before they reach production
5. **`/workflow:commit`** - Create clean, conventional commits
6. **`/workflow:session-end`** - Save accumulated knowledge for next time

The session memory system (`AI_CONTEXT.md`) is **tool-agnostic** - it works with any AI assistant, not just Claude Code.

## Skills Deep Dive

### git-workflow

Provides comprehensive Git conventions:
- Conventional Commits format (feat, fix, refactor, etc.)
- Branch naming patterns (`feat/TICKET-123_description`)
- Pull request standards
- Commit discipline best practices
- No AI attribution policy

**Invoke when:** Creating commits, branches, or pull requests

### openapi-spec-generation

Complete OpenAPI 3.1 specification patterns:
- Design-first and code-first approaches
- Schema validation and linting
- SDK generation (TypeScript, Python, Go)
- API documentation portals
- Request/response examples

**Invoke when:** Working with REST APIs, generating docs, or creating client SDKs

## Philosophy

**Tool-specific, convention-agnostic:**
- Commands use Claude Code features (subagents, Task tool, skills system)
- Underlying conventions (Git, architecture, workflow) are universal
- Project `AI_CONTEXT.md` files work with any AI tool

**No AI attribution:**
- Clean commits that read as human-written
- No "Generated with Claude Code" signatures
- Professional codebase presentation

## Pairing Recommendations

Works great with:
- **claude-laravel** - Laravel/PHP development skills
- Framework-specific plugins for your stack
- Language-specific linting/formatting tools

## License

MIT

## Contributing

Issues and pull requests welcome at [github.com/darkmodesyndicate/claude-workflow](https://github.com/darkmodesyndicate/claude-workflow)
