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
└── directives/           ← Single source of truth for all directive files
        directory.md
        {name}.md         ← e.g. billing.md — the complete directive file (spec + intelligence)
```

---

## Key Conventions

- **Directives** are the core unit of work. Each directive lives under `.claude/{name}-directive/`. They are protected — never overwrite without explicit user instruction.
- **`directives/{name}.md`** is the single directive file. It is the complete source of truth for that directive — human-readable specification (purpose, scope, ownership, deliverables) AND operational intelligence (requirements, orchestration, execution steps, self-anneal log). Named after the directive itself — e.g. `billing.md` for the billing directive. One file, one location. Created automatically by `/setup {name}`.
- **`.claude/{name}-directive/`** is the operational workspace for the directive. It contains the subdirectories (`scripts/`, `logs/`, `reports/`, `references/`, `.tmp/`) and a `directory.md`. There is no duplicate of the directive file here — the single source of truth lives in `directives/`.
- **`scripts/`** inside each directive workspace holds deterministic execution tools. Check here before writing new code. Scripts handle API calls, data processing, and file operations — Claude handles decisions.
- **`directory.md`** files are mandatory in **every** directory without exception — including leaf directories. They explain purpose, expected contents, and usage guidelines. If one is missing, create it before proceeding.
- **`session-context.md`** persists context between sessions. Updated automatically by `/analyze`.
- **`common/knowledge/`** is the source of truth for project-wide facts. Starts empty — populate as the project grows.
- **Never delete** `directory.md` files — they are Claude's map of the project.

---

## The 3-Layer Architecture

Every directive in the ACO Framework operates across three layers. Understanding this separation is essential to working correctly.

| Layer | Name | What it means |
|---|---|---|
| **Layer 1** | Directive | The *what*. SOPs written in Markdown. `directives/{name}.md` defines goals, inputs, scripts to use, outputs, edge cases, and deliverable destinations. |
| **Layer 2** | Orchestration | The *decide*. This is Claude's role. Read directives, call scripts in the right order, handle errors, ask for clarification, update directives with learnings. Claude is the intelligent glue between intent and execution. |
| **Layer 3** | Execution | The *do*. Deterministic scripts in `scripts/`. Handle API calls, data processing, file operations. Reliable, testable, fast. |

**Why this matters:** If Claude does everything itself, errors compound. 90% accuracy per step = 59% success over 5 steps. Push complexity into deterministic scripts. Claude focuses on decision-making.

---

## Operating Principles

These principles apply **framework-wide** across all directives. They cannot be overridden at the directive level.

### 1. Check for scripts before writing new ones
Before writing a script, check the directive's `scripts/` directory. Only create a new script if none exists that covers the need. Reuse and improve over creation.

### 2. Self-anneal when things break
When a script or execution step fails:
1. Read the error message and stack trace carefully
2. Fix the script and test it again
3. **Exception:** If the fix involves paid API calls, tokens, or credits — stop and check with the user first
4. Update the directive's **Self-Anneal Log** with what was learned (API limits, timing, edge cases, better approaches)
5. The system is now stronger than before

Errors are not failures. They are learning opportunities that make the directive more reliable over time.

### 3. Directives are living documents — but protected
Directives must be continuously improved as knowledge is gained. When you discover API constraints, better approaches, common errors, or timing expectations — update the directive.

**However:** Never create or overwrite a directive without explicit user instruction. Directives are the instruction set. They must be preserved and improved over time, not casually replaced.

### 4. Deliverables vs Intermediates
Every directive must specify clearly where its outputs live.

- **Intermediates:** Temporary files needed during processing. Always go in `.tmp/`. Never committed. Always regeneratable.
- **Deliverables:** Final outputs for the user. Must be explicitly declared in the directive's `Deliverables` section with their destination — local path, cloud service (e.g. Google Sheets, Azure Blob, S3), or both.

Local files are for processing only. If a deliverable lives in a cloud service, document the exact location so any session can find it.

### 5. Environment variables and credentials
- API keys, tokens, and secrets go in `.env` — never hardcoded in scripts
- `.env` is always git-ignored
- Credential files (e.g. `credentials.json`, `token.json`) are always git-ignored
- Document what variables are required in the directive's `Execution` section

---

## Self-Annealing Loop

When something breaks, follow this loop without exception:

```
1. Fix the script or tool
2. Test it — confirm it works
3. Update the directive's Self-Anneal Log with what changed and why
4. System is now stronger
```

This loop is what separates a brittle one-time automation from a reliable, improving system.

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
3. Review `.claude/common/knowledge/` files — check what exists and read what is relevant.
4. If working within a directive, read its file in `directives/{name}.md` before taking any action. Pay attention to the Orchestration, Execution, and Deliverables sections.
5. Check the directive's `scripts/` before writing any new code — reuse existing scripts.
6. If `directory.md` is missing from any directory, create it before proceeding.

---

## On Session End

Run `/analyze` to generate a full conversation summary and automatically save it to `.claude/session-context.md`. This captures:
- What was accomplished
- Key technical decisions and file changes
- Any open questions or blockers
- Next recommended actions

The output of `/analyze` overwrites `session-context.md` and serves as the handoff document for the next session.
