# Contributing

Thanks for helping improve harness-engineering.

## What belongs here

Please submit resources that are directly useful for designing, evaluating, or
operating agent harnesses. Good additions usually focus on one or more of:

- Context engineering and working-state management
- Tool design, tool calling, and environment control
- Evals, grading, benchmarking, or observability
- Long-running agents, resumability, retries, or orchestration
- Repo-local instructions such as `AGENTS.md`, specs, or workflow scaffolding
- Reference implementations that make harness design inspectable

Generic AI news, model launch posts, or broad agent-framework marketing pages
usually do not belong unless they contain concrete harness-level guidance.

## Quality bar

When proposing a new entry, prefer resources that are:

- Primary sources or original technical write-ups
- Non-duplicative with an existing entry
- Still available and reachable
- Specific enough that the description can explain why the resource matters

## Entry format

Please follow this format:

```md
- [Name](https://example.com) - Short description focused on why this matters for harness engineering.
```

Keep descriptions concise and practical. Explain the harness angle, not just the
topic.

## Placement

- Put the entry in the most specific section that fits.
- If a new section is genuinely needed, keep the section title short and broad
  enough to support future additions.
- Avoid adding the same resource to multiple sections.

## Before opening a PR

- Confirm the link works.
- Confirm the resource is actually about harness-relevant concerns.
- Confirm the description is accurate and not promotional.
- Check for duplicates in the README.
- Keep the diff focused.

## Pull requests

Small, focused pull requests are easiest to review.

If you are adding several links at once, include a short note explaining the
theme that connects them and why they belong in the chosen section.
