# CLAUDE.md — ACO Framework Project Intelligence

This file is automatically loaded by Claude Code at the start of every session.
It defines project conventions, directory structure, and available commands.

---

## Project Overview

This project follows the **ACO Framework** (Azure Cloud Operations) — a structured, directive-based architecture
where each feature domain or workflow is encapsulated in its own **directive** under `.claude/`.

Every directive has its own isolated workspace (logs, references, scripts, tmp) while
sharing common knowledge (conventions, dependencies, security, etc.) via `.claude/common/`.

---

## Directory Structure

```
project-root/
│   .gitattributes
│   .gitignore
│   CHANGELOG.md          ← Track all notable changes here
│   CLAUDE.md             ← You are here
│   README.md             ← Project overview for humans
│
├── .claude/
│   │   directory.md      ← Explains the .claude/ workspace
│   │   session-context.md← Persistent session state & notes
│   │   settings.json     ← Shared Claude Code settings
│   │   settings.local.json ← Local overrides (git-ignored)
│   │
│   ├── commands/         ← Custom Claude Code slash commands
│   │       directory.md
│   │
│   ├── common/           ← Shared knowledge across all directives
│   │   │   directory.md
│   │   ├── analysis/     ← Analytical outputs & scratch work
│   │   │       directory.md
│   │   ├── knowledge/    ← Living documentation files (populated as needed)
│   │   │       directory.md
│   │   └── reports/      ← Generated reports output
│   │           directory.md
│   │
│   ├── {name}-directive/ ← One per feature domain or workflow
│   │   │   directive.md  ← Central intelligence: requirements, orchestration, context
│   │   │   directory.md
│   │   ├── .tmp/         ← Ephemeral working files
│   │   │       directory.md
│   │   ├── logs/         ← Execution & audit logs
│   │   │       directory.md
│   │   ├── references/   ← External docs, specs, links
│   │   │       directory.md
│   │   ├── reports/      ← Produced outputs & deliverables
│   │   │       directory.md
│   │   └── scripts/      ← Automation scripts for this directive
│   │           directory.md
│   │
│   └── ...               ← Additional directives as needed
│
└── directives/           ← Directive definition files — one per directive
        directory.md
        {name}.md         ← e.g. billing.md, auth.md — created by /setup {name}
```

---

## Key Conventions

- **Directives** are the core unit of work. Each directive lives under `.claude/{name}-directive/`.
- **`directives/{name}.md`** is the directive definition file. It lives in the `directives/` folder at the project root and serves as the human-readable specification — purpose, scope, and ownership — for that directive. Created automatically by `/setup {name}`.
- **`.claude/{name}-directive/directive.md`** is the central intelligence file for the directive workspace. It holds requirements, orchestration logic, execution steps, and running context. Always read it before working on a directive.
- **`directory.md`** files are mandatory in **every** directory without exception — including leaf directories like `.tmp/`, `logs/`, `references/`, `reports/`, and `scripts/`. They explain the purpose of that directory, its expected contents, and usage guidelines. Always keep them updated. If one is missing, create it before proceeding.
- **`session-context.md`** is used to persist important context between sessions. Update it when significant decisions are made.
- **`common/knowledge/`** files are the source of truth for project-wide facts. The directory starts empty — add files here as your project knowledge grows. Reference them before making assumptions.
- **Never delete** `directory.md` files — they are Claude's map of the project.

---

## Available Commands

| Command | Description |
|---|---|
| `/setup` | Scaffold the full ACO framework skeleton in the current project |
| `/setup $DIRECTIVE_NAME` | Add a new named directive (e.g. `/setup billing`) |
| `/analyze` | Summarize the full conversation context and save it to `session-context.md` |
| `/reflect` | Analyze CLAUDE files and suggest improvements to instructions, commands, and config |

---

## On Session Start

1. Read this file (done automatically).
2. Check `.claude/session-context.md` for carry-over notes from prior sessions.
3. Review `.claude/common/knowledge/` files before writing any code — check what knowledge files exist and read any that are relevant.
4. If working within a directive, read its `directive.md` before taking any action.
5. If `directory.md` is missing from any directory, create it before proceeding.

---

## On Session End

Run `/analyze` to generate a full conversation summary and automatically save it to `.claude/session-context.md`. This captures:
- What was accomplished
- Key technical decisions and file changes
- Any open questions or blockers
- Next recommended actions

The output of `/analyze` overwrites `session-context.md` and serves as the handoff document for the next session.
