# Cursor Workflow

A collection of reusable Cursor IDE configurations — custom agents, skills, and rules — that enforce consistent engineering standards and automate common development workflows.

## What's Inside

### Rules

Always-applied workspace rules that every agent and session follows automatically.

| Rule | Description |
|------|-------------|
| `engineering` | Core engineering standards: small reviewable changes, security hygiene, accessibility, documentation, and reversibility. |
| `testing` | Testing conventions: co-located test files, table-driven tests, coverage expectations, isolation, and performance benchmarks. |

### Skills

Step-by-step workflows the agent follows when triggered by a relevant request.

| Skill | Trigger | Description |
|-------|---------|-------------|
| `add-endpoint` | "Add an API endpoint for ..." | Scaffolds a backend endpoint with route, handler, validation, tests, and docs — following existing project patterns. |
| `migration-plan` | "Plan a migration for ..." | Produces a full migration document with steps, rollback plan, validation queries, and risk assessment. |
| `pr-description` | "Generate a PR description" | Analyzes the current branch's diff and commits, then fills in a standardized PR description template. |
| `refactor-module` | "Refactor this module ..." | Guides an incremental refactor that preserves behavior, keeps tests green at every step, and verifies no API breakage. |
| `release-checklist` | "Run the release checklist" | Walks through a pre-release gate: tests, static analysis, database migrations, config, performance, docs, and deployment readiness. |
| `security-review` | "Do a security review of ..." | Performs a focused security audit covering input validation, auth, data protection, access control, and dependencies. |

### Agents

Specialized agent personas with defined responsibilities, output formats, and behavioral guidelines.

| Agent | Role |
|-------|------|
| `planner` | Breaks complex requests into scoped implementation plans and delegates to specialist agents. |
| `implementer` | Writes minimal, correct code changes that follow existing codebase patterns. |
| `reviewer` | Reviews diffs for correctness, security, maintainability, and missing tests. |
| `test-writer` | Writes targeted tests — happy path, error paths, edge cases — following project conventions. |
| `verifier` | Validates completed work by running lints, tests, and checking for regressions and edge cases. |
| `backend` | Implements APIs, services, and data access layers with proper validation and error handling. |
| `frontend` | Builds accessible, responsive, performant UI components consistent with the project's design system. |
| `migration` | Plans and implements safe, reversible database migrations with rollback and validation. |
| `docs` | Creates and updates documentation — READMEs, API docs, changelogs, and inline comments. |
| `performance` | Profiles, benchmarks, and optimizes code with evidence-based measurements. |

## Repository Structure

```
.cursor/
├── agents/
│   ├── backend.md
│   ├── docs.md
│   ├── frontend.md
│   ├── implementer.md
│   ├── migration.md
│   ├── performance.md
│   ├── planner.md
│   ├── reviewer.md
│   ├── test-writer.md
│   └── verifier.md
├── rules/
│   ├── engineering.mdc
│   └── testing.mdc
└── skills/
    ├── add-endpoint/SKILL.md
    ├── migration-plan/SKILL.md
    ├── pr-description/SKILL.md
    ├── refactor-module/SKILL.md
    ├── release-checklist/SKILL.md
    └── security-review/SKILL.md
```

## Usage

Clone or copy the `.cursor/` directory into any project's root. Rules apply automatically to every session. Skills activate when the agent recognizes a matching request. Agents are available as custom agent types in Cursor's agent selector.

```bash
# Copy into an existing project
cp -r .cursor/ /path/to/your/project/
```

To use a subset, copy only the directories you need — `rules/`, `skills/`, and `agents/` are independent of each other.

## Customization

- **Rules** (`.mdc` files) use YAML frontmatter with `alwaysApply: true` to stay active across all sessions. Set `alwaysApply: false` and add a `globs` pattern to scope a rule to specific files.
- **Skills** (`SKILL.md` files) are self-contained workflow guides. Edit the steps or template to match your team's process.
- **Agents** (`.md` files) define persona, responsibilities, and output format. Adjust the tone, checklist items, or output structure to fit your team's review culture.
