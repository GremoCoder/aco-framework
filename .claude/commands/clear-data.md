# ACO Framework — Clear Directive Data

Delete all generated data files from a named directive's workspace, leaving the
structure and authored content intact.

**Usage:**
- `/clear-data $ARGUMENTS` — clear data files from the `$ARGUMENTS` directive

---

## Instructions

### STEP 1 — Validate Input

If `$ARGUMENTS` is empty, print an error and stop:

```
❌ Directive name required. Usage: /clear-data <name>
```

Set `DIRECTIVE = $ARGUMENTS` (trim whitespace).

Check that `.claude/$DIRECTIVE-directive/` exists. If it does not, print an error and stop:

```
❌ Directive workspace not found: .claude/$DIRECTIVE-directive/
   Run /setup $DIRECTIVE to create it first.
```

---

### STEP 2 — Identify Files to Delete

Scan the following directories inside `.claude/$DIRECTIVE-directive/`:

| Directory | Action |
|---|---|
| `.tmp/` | Delete **all files** |
| `logs/` | Delete **all files** |
| `reports/` | Delete **all files** |
| `references/` | **Skip** — contains manually authored reference material |
| `scripts/` | **Skip** — contains authored execution scripts |

**Rules:**
- Delete files only — never delete directories or `directory.md` files.
- If a directory is empty (only contains `directory.md`), skip it silently.
- Do not touch `directives/$DIRECTIVE.md` — that is the directive spec and must never be cleared.
- Do not touch any `directory.md` file anywhere.

---

### STEP 3 — Confirm Before Deleting

Before deleting anything, print a summary of what will be removed and ask for confirmation:

```
🗑️  Files to be deleted from $DIRECTIVE directive:

  .tmp/
    - <file1>
    - <file2>

  logs/
    - <file3>

  reports/
    - <file4>

  (nothing to clear in references/ or scripts/)

Proceed? [y/N]
```

If there are no files to delete, print:

```
✅ Nothing to clear — $DIRECTIVE directive workspace is already clean.
```

and stop.

Wait for the user to confirm. If the user says anything other than `y` or `yes` (case-insensitive), print:

```
❌ Aborted. No files were deleted.
```

and stop.

---

### STEP 4 — Delete Files

Delete each identified file. Use the Bash tool to remove files.

---

### STEP 5 — Summary

Print a confirmation of what was deleted:

```
✅ $DIRECTIVE directive workspace cleared.

Deleted:
  - [list of deleted files]

Preserved:
  - All directory.md files
  - directives/$DIRECTIVE.md (directive spec)
  - directives/$DIRECTIVE.client.md (client overlay)
  - references/ (manual content)
  - scripts/ (authored scripts)
```
