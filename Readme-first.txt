================================================================================
 ACO FRAMEWORK — README FIRST
 Azure Cloud Operations Framework
 How to set up Claude Code with the ACO Framework in a new project
================================================================================

WHAT YOU HAVE
-------------
This package contains four files that together give Claude Code a structured,
directive-based project workspace:

  CLAUDE.md                        → Project intelligence file. Claude Code
                                     loads this automatically on every session.

  .claude/commands/setup.md        → The /setup slash command. Run this once
                                     inside Claude Code to scaffold the full
                                     directory skeleton.

  .claude/commands/analyze.md      → The /analyze slash command. Run at the end
                                     of any session to capture a full context
                                     summary and save it to session-context.md.

  .claude/commands/reflect.md      → The /reflect slash command. Run to analyze
                                     CLAUDE files and get improvement suggestions
                                     for instructions, commands, and config.


--------------------------------------------------------------------------------
STEP 1 — COPY FILES INTO YOUR PROJECT
--------------------------------------------------------------------------------

Copy all files into your new project, preserving the directory structure:

  your-project/
  ├── CLAUDE.md                          ← place here (project root)
  └── .claude/
      └── commands/
          ├── analyze.md                 ← place here
          ├── reflect.md                 ← place here
          └── setup.md                   ← place here


  On Windows:
    1. Copy CLAUDE.md to your project root folder.
    2. Inside your project, create the folder:  .claude\commands\
    3. Copy setup.md, analyze.md and reflect.md into that folder.

  On macOS / Linux:
    From the directory containing this file, run:

      cp CLAUDE.md /path/to/your-project/
      mkdir -p /path/to/your-project/.claude/commands
      cp .claude/commands/setup.md /path/to/your-project/.claude/commands/
      cp .claude/commands/analyze.md /path/to/your-project/.claude/commands/
      cp .claude/commands/reflect.md /path/to/your-project/.claude/commands/


--------------------------------------------------------------------------------
STEP 2 — OPEN THE PROJECT IN CLAUDE CODE
--------------------------------------------------------------------------------

  Navigate to your project root in your terminal and start Claude Code:

      cd /path/to/your-project
      claude


--------------------------------------------------------------------------------
STEP 3 — RUN THE SETUP COMMAND
--------------------------------------------------------------------------------

  Inside the Claude Code session, type:

      /setup

  Claude will scaffold the full ACO Framework directory skeleton, including:

    ✔ Root files         README.md, CHANGELOG.md, .gitignore, .gitattributes
    ✔ .claude/           Workspace with session-context.md and settings files
    ✔ .claude/commands/  Slash commands directory
    ✔ .claude/common/    Shared directories — analysis/, knowledge/, reports/ (all empty)
    ✔ directives/        Directive definitions directory (empty until /setup <n> is run)

  All existing files are left untouched — /setup skips anything already present.


--------------------------------------------------------------------------------
STEP 4 — ADD YOUR FIRST DIRECTIVE (OPTIONAL)
--------------------------------------------------------------------------------

  A directive is an isolated workspace for a feature domain or workflow.
  To create one, run /setup with a name:

      /setup billing
      /setup auth
      /setup reporting

  This creates two things for each directive:

  1. A definition file at the project level:

                   directives/
                   └── {name}.md         (human-readable spec — purpose, scope, owner)

  2. A full workspace under .claude/:

                   .claude/{name}-directive/
                   ├── directive.md      (central intelligence — requirements,
                   │                      orchestration, execution, context)
                   ├── directory.md      (purpose & contents — pre-filled)
                   ├── .tmp/             (ephemeral working files)
                   ├── logs/             (execution & audit logs)
                   ├── references/       (external specs and docs)
                   ├── reports/          (produced outputs & deliverables)
                   └── scripts/          (automation scripts)

  You can run /setup <n> as many times as needed for different directives.


--------------------------------------------------------------------------------
STEP 5 — FILL IN YOUR PROJECT DETAILS
--------------------------------------------------------------------------------

  After scaffolding, Claude will prompt you with next steps. At minimum:

  1. Edit README.md
     Add your project name and description.

  2. Populate .claude/common/knowledge/
     This directory starts empty. Create .md files here as your project knowledge
     grows — e.g. conventions.md, dependencies.md, environment-overview.md.
     Claude reads these files before making decisions, so add content here early.

  3. Edit .claude/session-context.md
     Add any carry-over notes at the start of important sessions.


--------------------------------------------------------------------------------
HOW IT WORKS — QUICK REFERENCE
--------------------------------------------------------------------------------

  File / Command              What it does
  --------------------------  --------------------------------------------------
  CLAUDE.md                   Loaded automatically by Claude Code every session.
                              Gives Claude the project map and conventions.

  /setup                      Scaffolds the full ACO skeleton (safe to re-run).

  /setup <name>               Scaffolds skeleton + adds a new named directive.

  /analyze                    Summarizes the full conversation context and saves
                              it to .claude/session-context.md. Run at session
                              end as the handoff document for the next session.

  /reflect                    Analyzes CLAUDE.md, commands, and config files to
                              identify improvements. Works interactively —
                              presents suggestions and waits for your approval
                              before making any changes.

  directive.md (per directive) Central intelligence for that directive. Holds
                              requirements, orchestration, execution steps, and
                              running context. Read before working on a directive.

  directory.md (everywhere)   Explains each folder's purpose to Claude.
                              Always keep these updated.

  session-context.md          Carries notes between sessions. Update at session
                              end with decisions made and next actions.

  common/knowledge/*.md       Source of truth for project-wide facts. Claude
                              reads these before making decisions.


--------------------------------------------------------------------------------
QUESTIONS OR ISSUES
--------------------------------------------------------------------------------

  If /setup is not recognized in Claude Code, verify that setup.md is located
  exactly at:   .claude/commands/setup.md   (relative to your project root)

  Claude Code only picks up slash commands from that specific directory.

================================================================================
