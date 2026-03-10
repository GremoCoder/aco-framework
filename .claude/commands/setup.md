# ACO Framework — Project Scaffold Setup

Scaffold the full ACO (Azure Cloud Operations) Framework directory skeleton in the current project.
If a directive name is provided, also create a new directive with that name.

**Usage:**
- `/setup` — scaffold full skeleton
- `/setup $ARGUMENTS` — scaffold full skeleton + create a new directive named `$ARGUMENTS`

---

## Instructions

You are setting up a new ACO Framework project. Follow these steps carefully and in order.

### STEP 1 — Safety Check

Before creating anything, check which files and directories already exist.
For every item below, **skip it silently if it already exists**. Only create what is missing.
Print a summary at the end of what was created vs. skipped.

---

### STEP 2 — Scaffold Root Files

Create the following files in the **project root** if they don't exist:

**`README.md`**
```markdown
# Project Name

> Replace this with a brief description of the project.

## Getting Started

_Add setup instructions here._

## Architecture

See `.claude/directory.md` for the full project structure overview.
```

**`CHANGELOG.md`**
```markdown
# Changelog

All notable changes to this project will be documented here.

## [Unreleased]

### Added
- Initial project scaffold via ACO Framework
```

**`.gitignore`** — append these lines if not already present:
```
.claude/settings.local.json
.claude/**//.tmp/
```

**`.gitattributes`** — create with:
```
* text=auto
*.md text eol=lf
```

---

### STEP 3 — Scaffold `.claude/` Workspace

Create the following structure under `.claude/`:

#### `.claude/session-context.md`
```markdown
# Session Context

This file carries important context between Claude Code sessions.
Update it at the end of every session.

---

## Last Session Summary

_Nothing recorded yet._

## Open Questions / Blockers

_None._

## Next Recommended Actions

_None._
```

#### `.claude/settings.json`
```json
{
  "hooks": {}
}
```

#### `.claude/settings.local.json`
```json
{
  "// note": "This file is git-ignored. Add your local overrides here."
}
```

#### `.claude/directory.md`
```markdown
# Directory: .claude/

## Purpose

This is the Claude Code workspace for the project.
It contains all AI-assisted tooling, directives, shared knowledge, and session state.

## Contents

| Name | Type | Purpose |
|---|---|---|
| `CLAUDE.md` | file | Root-level instructions loaded automatically by Claude Code |
| `session-context.md` | file | Persistent notes carried between sessions |
| `settings.json` | file | Shared Claude Code hook and permission settings |
| `settings.local.json` | file | Local overrides — git-ignored |
| `commands/` | directory | Custom slash commands available in Claude Code |
| `common/` | directory | Shared knowledge and analysis used across all directives |
| `*-directive/` | directory | One isolated workspace per feature domain or workflow |

## Guidelines

- Never delete `directory.md` files — they are navigation aids for Claude.
- Keep `session-context.md` updated at the end of every session.
- Add new directives using the `/setup <name>` command.
```

---

### STEP 4 — Scaffold `.claude/commands/`

#### `.claude/commands/directory.md`
```markdown
# Directory: .claude/commands/

## Purpose

Contains custom Claude Code slash commands for this project.
Each `.md` file in this directory becomes a `/command-name` available in Claude Code.

## Contents

| File | Command | Purpose |
|---|---|---|
| `analyze.md` | `/analyze` | Summarize conversation context and save to session-context.md |
| `reflect.md` | `/reflect` | Analyze CLAUDE files and suggest improvements to instructions and config |
| `setup.md` | `/setup` | Scaffold the ACO framework skeleton |

## How to Add a Command

1. Create a new `.md` file here named after your command (e.g. `review.md` → `/review`).
2. Write the instructions in natural language.
3. Use `$ARGUMENTS` anywhere in the file to capture user-provided arguments.

## Guidelines

- Keep commands focused on a single task.
- Document each command in this `directory.md` when you add it.
```

---

### STEP 5 — Scaffold `.claude/common/`

#### `.claude/common/directory.md`
```markdown
# Directory: .claude/common/

## Purpose

Shared resources used across all directives in this project.
Contains living knowledge documents and analytical outputs.

## Contents

| Name | Type | Purpose |
|---|---|---|
| `analysis/` | directory | Scratch space for analytical work and explorations |
| `knowledge/` | directory | Source-of-truth documentation files |
| `reports/` | directory | Generated reports and summaries |

## Guidelines

- Always check `knowledge/` files before making assumptions about the project.
- Do not store directive-specific content here — use the relevant directive's directory instead.
```

#### `.claude/common/analysis/` — create directory (empty, no files needed yet)

#### `.claude/common/reports/` — create directory (empty, no files needed yet)

#### `.claude/common/knowledge/directory.md`
```markdown
# Directory: .claude/common/knowledge/

## Purpose

The single source of truth for project-wide facts, conventions, and context.
Claude should read relevant files here before making decisions or writing code.

## Contents

This directory is intentionally empty at scaffold time.
Add `.md` files here as your project knowledge grows. Common files to create:

| File | Purpose |
|---|---|
| `conventions.md` | Coding standards, naming rules, patterns to follow |
| `dependencies.md` | Key libraries, tools, and version constraints |
| `environment-overview.md` | Infrastructure, environments, and deployment targets |
| `networking.md` | APIs, endpoints, network topology |
| `resources.md` | Links to external docs, wikis, dashboards |
| `security.md` | Security policies, secrets handling, access rules |
| `change-log.md` | Record of significant architectural or process changes |

## Guidelines

- Keep files concise and accurate — they are read on every session.
- Only create a file when you have real content to put in it.
- Update `change-log.md` whenever a significant decision is made.
```

#### `.claude/common/knowledge/` — create directory (empty, no files needed yet)

---

### STEP 6 — Scaffold `directives/`

#### `directives/directory.md`
```markdown
# Directory: directives/

## Purpose

Contains the directive definition file for each feature domain or workflow in this project.
Each `.md` file here is the human-readable specification for a directive — its purpose,
scope, and ownership.

Each definition file corresponds to a `{name}-directive/` workspace under `.claude/`
and is created automatically when you run `/setup {name}`.

## Contents

| File | Directive | Purpose |
|---|---|---|
| _none yet_ | — | Definition files are added here automatically by `/setup <n>` |

## Guidelines

- One definition file per directive — named `{name}.md` (e.g. `billing.md` for the billing directive).
- Keep definitions focused: purpose, scope, owner, and links to related resources.
- Do not store operational content here — that belongs in `.claude/{name}-directive/directive.md`.
```

---

### STEP 7 — Create Named Directive (if argument provided)

**Only run this step if `$ARGUMENTS` is not empty.**

Create the following structure under `.claude/$ARGUMENTS-directive/`:

#### `.claude/$ARGUMENTS-directive/directory.md`
```markdown
# Directory: .claude/$ARGUMENTS-directive/

## Purpose

> Replace this with a brief description of what this directive is responsible for.

## Contents

| Name | Type | Purpose |
|---|---|---|
| `directive.md` | file | Central intelligence — requirements, orchestration, execution, and context |
| `.tmp/` | directory | Ephemeral working files — not committed |
| `logs/` | directory | Execution logs and audit trail |
| `references/` | directory | External specs, docs, and links relevant to this directive |
| `reports/` | directory | Produced outputs — generated reports, summaries, and deliverables |
| `scripts/` | directory | Automation scripts scoped to this directive |

## Workflow

_Describe how this directive is typically used._

## Related Directives

_List any other directives this one depends on or interacts with._
```

Also create these files and subdirectories:

#### `.claude/$ARGUMENTS-directive/directive.md`
```markdown
# Directive: $ARGUMENTS

> One-sentence summary of what this directive does and why it exists.

---

## Requirements

Describe what this directive must accomplish. List functional and non-functional
requirements, acceptance criteria, or goals.

- [ ] _Requirement 1_
- [ ] _Requirement 2_
- [ ] _Requirement 3_

---

## Orchestration

Describe how this directive is structured and how its parts work together.
Include any sequencing, dependencies between steps, or decision points.

### Steps

1. _Step 1 — description_
2. _Step 2 — description_
3. _Step 3 — description_

### Dependencies

- **Requires:** _list other directives or resources this one depends on_
- **Produces:** _list outputs consumed by other directives or systems_

---

## Execution

Document how to run or invoke this directive. Include commands, scripts,
entry points, or manual steps.

```bash
# Example: run the main script for this directive
# .claude/$ARGUMENTS-directive/scripts/run.sh
```

### Scripts

| Script | Purpose |
|---|---|
| _script-name.sh_ | _what it does_ |

---

## Context

Capture running context, decisions made, and evolving understanding of this directive.
Update this section as work progresses.

### Decisions Log

| Date | Decision | Reason |
|---|---|---|
| _YYYY-MM-DD_ | _decision_ | _why_ |

### Open Questions

- _Question 1_

### Notes

_Any other context Claude or team members should know._
```

**Subdirectories to create:**
- `.claude/$ARGUMENTS-directive/.tmp/`
- `.claude/$ARGUMENTS-directive/logs/`
- `.claude/$ARGUMENTS-directive/references/`
- `.claude/$ARGUMENTS-directive/reports/`
- `.claude/$ARGUMENTS-directive/scripts/`

#### `directives/$ARGUMENTS.md`
```markdown
# $ARGUMENTS Directive

> One-sentence description of what this directive is responsible for.

---

## Purpose

_Describe the goal and scope of this directive. What problem does it solve?
What domain or workflow does it own?_

## Owner

_Who is responsible for this directive? (team, person, or role)_

## Scope

_What is in scope for this directive? What is explicitly out of scope?_

## Related Directives

| Directive | Relationship |
|---|---|
| _name_ | _depends on / produces for / shares context with_ |

## Resources

- _Link to specs, designs, or external documentation_

## Notes

_Any other information relevant to understanding this directive._
```

Then update `directives/directory.md` contents table to add a row for `$ARGUMENTS.md`.

---

### STEP 8 — Summary Report

After completing all steps, print a clear summary:

```
✅ ACO Framework scaffold complete.

Created:
  - [list of files/directories created]

Skipped (already existed):
  - [list of files/directories skipped]

Next steps:
  1. Edit README.md with your project description.
  2. Create knowledge files in .claude/common/knowledge/ as your project grows
     (e.g. conventions.md, environment-overview.md, dependencies.md).
  3. Run /setup <n> to add your first directive.
```
