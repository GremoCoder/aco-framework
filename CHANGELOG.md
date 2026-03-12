# Changelog

All notable changes to this project will be documented here.

## [Unreleased]

### Added
- Initial project scaffold via ACO Framework

### Changed
- Added `directives/*.client.md` to `.gitignore` to prevent accidental commit of client-sensitive data ← Added by the /reflect command
- Added `directives/*.client.md` to `.gitignore` block in `/setup` command so new projects inherit the protection ← Added by the /reflect command
- Fixed stale `/clear` usage line in `clear-data.md` → `/clear-data` ← Added by the /reflect command
- Added shared git permissions to `settings.json` (status, log, diff, commit, add, push) to reduce approval prompts ← Added by the /reflect command
- Added `directives/$DIRECTIVE.client.md` to preserved list in `/clear-data` Step 5 summary ← Added by the /reflect command
- Documented `.client.md` git-ignore rule in `CLAUDE.md` Operating Principles §5 ← Added by the /reflect command
