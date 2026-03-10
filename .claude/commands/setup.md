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
.claude/**/.tmp/
.env
credentials.json
token.json
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

#### `.claude/common/analysis/directory.md`
```markdown
# Directory: .claude/common/analysis/

## Purpose

Scratch space for analytical work, explorations, and intermediate findings
that are shared across directives. Use this directory to capture investigative
outputs before they are formalized into reports or knowledge files.

## Contents

This directory is intentionally empty at scaffold time.
Files are created here organically during analytical work. Common file types:

| File Pattern | Purpose |
|---|---|
| `{topic}-analysis.md` | Findings and notes from an investigation |
| `{topic}-comparison.md` | Side-by-side comparison of options or approaches |
| `{topic}-spike.md` | Time-boxed exploration of an unknown or risk area |

## Guidelines

- Files here are working documents, not final outputs. Move completed work to `reports/`.
- Prefix file names with a date or topic for easy scanning.
- Do not store directive-specific analysis here — use the relevant directive's workspace.
```

#### `.claude/common/reports/directory.md`
```markdown
# Directory: .claude/common/reports/

## Purpose

Stores finalized reports and summaries that are shared across directives.
These are polished outputs intended for review, sharing, or archiving —
distinct from the working documents in `analysis/`.

## Contents

This directory is intentionally empty at scaffold time.
Reports are generated here over the course of the project. Common file types:

| File Pattern | Purpose |
|---|---|
| `{topic}-report.md` | Formal written report on a topic or outcome |
| `{topic}-summary.md` | Condensed summary of findings or decisions |
| `{date}-status.md` | Periodic status or progress report |

## Guidelines

- Only place finalized content here. Use `analysis/` for work in progress.
- Name files descriptively so their purpose is clear without opening them.
- Do not store directive-specific reports here — use the relevant directive's `reports/` directory.
```

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

#### `.claude/common/knowledge/` — create directory (the `directory.md` above is its only file at scaffold time)

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

## Layer 1 — Requirements (What)

Describe what this directive must accomplish. List functional and non-functional
requirements, acceptance criteria, or goals.

- [ ] _Requirement 1_
- [ ] _Requirement 2_
- [ ] _Requirement 3_

---

## Layer 2 — Orchestration (Decide)

Claude's decision-making guide for this directive. Describes how the parts work
together, the sequencing of steps, dependencies, and how to handle edge cases.
Claude reads this section to understand what to do and in what order.

### Steps

1. _Step 1 — description_
2. _Step 2 — description_
3. _Step 3 — description_

### Dependencies

- **Requires:** _list other directives or resources this one depends on_
- **Produces:** _list outputs consumed by other directives or systems_

### Edge Cases

_Document known failure modes, API limits, timing constraints, and how to handle them._

---

## Layer 3 — Execution (Do)

Deterministic scripts that perform the actual work. Claude checks this section
before writing any new code — existing scripts must be reused and improved, not duplicated.

### Environment Variables

List all required `.env` variables this directive depends on:

| Variable | Purpose |
|---|---|
| _VAR_NAME_ | _what it is used for_ |

### Scripts

| Script | Purpose | Status |
|---|---|---|
| _script-name.sh_ | _what it does_ | 🔴 Not created |

```bash
# Entry point to run this directive
# .claude/$ARGUMENTS-directive/scripts/run.sh
```

---

## Deliverables

All outputs produced by this directive must be listed here with their destination.
Intermediates go in `.tmp/` and are never committed. Deliverables are final outputs.

| Deliverable | Type | Destination | Notes |
|---|---|---|---|
| _name_ | Local / Cloud / Both | _path or service URL_ | _format, access details_ |

> **Rule:** Local files are for processing only. If a deliverable lives in a cloud
> service, document the exact location so any session can find it without asking.

---

## Context

Running context, decisions made, and evolving understanding of this directive.
Updated as work progresses. Never overwritten without explicit user instruction.

### Decisions Log

| Date | Decision | Reason |
|---|---|---|
| _YYYY-MM-DD_ | _decision_ | _why_ |

### Self-Anneal Log

Record of every break-fix cycle. Each entry makes this directive stronger.

| Date | What broke | Root cause | Fix applied | Script updated? |
|---|---|---|---|---|
| _YYYY-MM-DD_ | _description_ | _cause_ | _what was changed_ | Yes / No |

### Open Questions

- _Question 1_

### Notes

_Any other context Claude or team members should know._
```

Also create the following subdirectories, each with a `directory.md`:

#### `.claude/$ARGUMENTS-directive/.tmp/directory.md`
```markdown
# Directory: .claude/$ARGUMENTS-directive/.tmp/

## Purpose

Ephemeral working space for the $ARGUMENTS directive.
Holds temporary files generated during execution that do not need to be committed
or persisted after the task is complete.

## Contents

This directory is always transient. Files here may be deleted at any time.

| File Pattern | Purpose |
|---|---|
| `*.tmp` | Temporary output from a script or tool |
| `*.json` | Intermediate data payloads during processing |
| `scratch-*.md` | Throwaway notes during active work |

## Guidelines

- Never commit files from this directory to source control (covered by `.gitignore`).
- Clean up this directory regularly to avoid confusion.
- If a file needs to persist, move it to `logs/`, `reports/`, or `references/`.
```

#### `.claude/$ARGUMENTS-directive/logs/directory.md`
```markdown
# Directory: .claude/$ARGUMENTS-directive/logs/

## Purpose

Execution logs and audit trail for the $ARGUMENTS directive.
Captures a chronological record of runs, outcomes, errors, and significant events
to support debugging, auditing, and continuity across sessions.

## Contents

This directory is intentionally empty at scaffold time.
Log files are written here during execution.

| File Pattern | Purpose |
|---|---|
| `{date}-run.log` | Output from a single execution run |
| `{date}-error.log` | Error output captured during a failed run |
| `{date}-audit.md` | Human-readable audit entry for a significant event |

## Guidelines

- Name log files with a date prefix for chronological sorting.
- Do not edit log files after they are written.
- Archive or prune old logs periodically to keep the directory manageable.
```

#### `.claude/$ARGUMENTS-directive/references/directory.md`
```markdown
# Directory: .claude/$ARGUMENTS-directive/references/

## Purpose

External and internal reference material scoped to the $ARGUMENTS directive.
Stores specs, documentation excerpts, API contracts, design documents, and
any other source material that informs how this directive is built or run.

## Contents

This directory is intentionally empty at scaffold time.
Add reference material here as the directive is developed.

| File Pattern | Purpose |
|---|---|
| `{name}-spec.md` | Specification or contract for a component or API |
| `{name}-design.md` | Design document or architectural decision record |
| `{name}-notes.md` | Notes from meetings, research, or external sources |

## Guidelines

- Keep references read-only — do not generate output into this directory.
- Prefer linking to external sources; only copy content here when offline access is needed.
- For project-wide references, use `.claude/common/knowledge/` instead.
```

#### `.claude/$ARGUMENTS-directive/reports/directory.md`
```markdown
# Directory: .claude/$ARGUMENTS-directive/reports/

## Purpose

Produced outputs and deliverables scoped to the $ARGUMENTS directive.
This is where finalized reports, generated summaries, and exported artifacts
from this directive are stored.

## Contents

This directory is intentionally empty at scaffold time.
Reports are written here as the directive produces outputs.

| File Pattern | Purpose |
|---|---|
| `{topic}-report.md` | Formal report generated by this directive |
| `{topic}-summary.md` | Condensed summary of an outcome or finding |
| `{date}-output.md` | Timestamped output from a specific execution |

## Guidelines

- Only place finalized content here. Use `.tmp/` for work in progress.
- For reports shared across directives, copy to `.claude/common/reports/`.
- Name files descriptively so their purpose is clear without opening them.
```

#### `.claude/$ARGUMENTS-directive/scripts/directory.md`
```markdown
# Directory: .claude/$ARGUMENTS-directive/scripts/

## Purpose

Deterministic execution tools scoped to the $ARGUMENTS directive (Layer 3).
Scripts here do the actual work — API calls, data processing, file operations.
Claude does not do this work directly; it orchestrates these scripts.

**Always check this directory before writing new code.** Reuse and improve
existing scripts rather than duplicating logic. Register every script in
`directive.md` under the Execution > Scripts table.

## Contents

This directory is intentionally empty at scaffold time.
Scripts are added here as the directive is built out.

| File Pattern | Purpose |
|---|---|
| `run.sh` | Main entry point — orchestrates the full directive workflow |
| `setup.sh` | One-time setup or dependency installation |
| `validate.sh` | Pre-run checks — inputs, credentials, environment |
| `cleanup.sh` | Post-run cleanup of `.tmp/` and ephemeral resources |
| `{action}.py` | Deterministic Python script for a specific operation |

## Guidelines

- Make all scripts executable (`chmod +x`).
- Include a usage comment block at the top of every script.
- Scripts must be reliable, testable, and well-commented.
- When a script is fixed via self-annealing, update both the script and the
  Self-Anneal Log in `directive.md`.
- Environment variables and API keys come from `.env` — never hardcoded.
- For scripts shared across directives, place them in `.claude/common/`.
```

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

## Deliverables

_Where does the output of this directive live? Be explicit — local path, cloud service,
or both. This must be defined before work begins._

| Deliverable | Destination | Format | Notes |
|---|---|---|---|
| _name_ | _local path or cloud service URL_ | _file type / format_ | _access or sharing details_ |

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
