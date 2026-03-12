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
| `discover.md` | discover | Definition files are added here automatically by `/setup <n>` |
| `assess.md` | assess | Definition files are added here automatically by `/setup <n>` |
| `finops.md` | finops | Definition files are added here automatically by `/setup <n>` |

## Guidelines

- One file per directive — named `{name}.md` (e.g. `billing.md` for the billing directive).
- This is the single source of truth: spec, requirements, orchestration, execution, deliverables, and self-anneal log — all in one file.
- The corresponding workspace lives at `.claude/{name}-directive/` but does NOT contain a copy of this file.
- Always edit the file here in `directives/`. Never duplicate it.
- To clear generated data (`.tmp/`, `logs/`, `reports/`) from a directive workspace, run `/clear-data {name}`.
