# Directory: .claude/discover-directive/scripts/

## Purpose

Deterministic execution tools scoped to the discover directive (Layer 3).
Scripts here do the actual work — API calls, data processing, file operations.
Claude does not do this work directly; it orchestrates these scripts.

**Always check this directory before writing new code.** Reuse and improve
existing scripts rather than duplicating logic. Register every script in
`discover.md` under the Execution > Scripts table.

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
  Self-Anneal Log in `discover.md`.
- Environment variables and API keys come from `.env` — never hardcoded.
- For scripts shared across directives, place them in `.claude/common/`.
