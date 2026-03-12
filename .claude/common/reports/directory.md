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
