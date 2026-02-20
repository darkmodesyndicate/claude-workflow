# Code Review

I'll review your code for potential issues.

Let me create a checkpoint before detailed analysis:
```bash
git add -A  
git commit -m "Pre-review checkpoint" || echo "No changes to commit"
```

I'll launch all review sub-agents **simultaneously in a single message** - do not wait for one to finish before launching the next. All four must be dispatched at the same time and their results aggregated after all have returned:

- **Security sub-agent**: Credential exposure, input validation, SQL injection, XSS, CSRF, authorization gaps
- **Performance sub-agent**: N+1 queries, missing eager loading, missing indexes, cache opportunities
- **Quality sub-agent**: Code complexity, duplication, naming, adherence to project conventions
- **Architecture sub-agent**: Layer separation, dependency direction, SOLID principles, scalability

Aggregate all results after all four agents have returned, then present a unified report ordered by severity.

I'll examine files using the Read and Grep tools to analyze:
1. **Security Issues** - credential exposure, input validation
2. **Logic Problems** - error handling, edge cases  
3. **Performance Concerns** - inefficient patterns, bottlenecks
4. **Code Quality** - complexity, maintainability

When I find multiple issues, I'll create a todo list to address them systematically.

For each issue, I'll:
- Show exact location with file references
- Explain the problem and potential impact
- Provide specific remediation steps
- Prioritize by severity and effort

After review, I'll ask: "Create GitHub issues for critical findings?"
- Yes: I'll create prioritized issues with detailed descriptions
- Todos only: I'll maintain local tracking for resolution
- Summary: I'll provide actionable report

**Important**: I will NEVER:
- Add "Co-authored-by" or any Claude signatures to commits
- Add "Created by Claude" or any AI attribution to issues
- Include "Generated with Claude Code" in any output
- Modify git config or repository settings
- Add any AI/assistant signatures or watermarks
- Use emojis in commits, PRs, issues, or git-related content

This focuses on real problems that impact your application's reliability and maintainability.