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
