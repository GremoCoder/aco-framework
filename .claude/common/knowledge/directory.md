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
