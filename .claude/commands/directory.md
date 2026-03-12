# Directory: .claude/commands/

## Purpose

Contains custom Claude Code slash commands for this project.
Each `.md` file in this directory becomes a `/command-name` available in Claude Code.

## Contents

| File | Command | Purpose |
|---|---|---|
| `analyze.md` | `/analyze` | Summarize conversation context and save to session-context.md |
| `clear-data.md` | `/clear-data` | Delete generated data files from a directive's workspace |
| `reflect.md` | `/reflect` | Analyze CLAUDE files and suggest improvements to instructions and config |
| `setup.md` | `/setup` | Scaffold the ACO framework skeleton |

## How to Add a Command

1. Create a new `.md` file here named after your command (e.g. `review.md` → `/review`).
2. Write the instructions in natural language.
3. Use `$ARGUMENTS` anywhere in the file to capture user-provided arguments.

## Guidelines

- Keep commands focused on a single task.
- Document each command in this `directory.md` when you add it.
