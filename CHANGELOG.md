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
- Added `/clear-data` entry to `commands/directory.md` template in `/setup` STEP 4 — was missing despite command existing ← Added by the /reflect command
- Updated `/setup` STEP 7 workspace `directory.md` template to reference both `{name}.md` and `{name}.client.md` ← Added by the /reflect command
- Updated `/setup` STEP 8 next-steps summary to note that `/setup <n>` creates both files ← Added by the /reflect command
- Updated `Readme-first.txt` STEP 4 to show `{name}.client.md` in the directive tree ← Added by the /reflect command
- Updated `Readme-first.txt` STEP 5 to add populating `.client.md` as a required setup step ← Added by the /reflect command
- Updated `Readme-first.txt` Quick Reference to document `{name}.client.md` alongside the framework SOP ← Added by the /reflect command
