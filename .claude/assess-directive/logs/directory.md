# Directory: .claude/assess-directive/logs/

## Purpose

Execution logs and audit trail for the assess directive.
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
