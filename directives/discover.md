# discover Directive

> One-sentence summary of what this directive does and why it exists.

---

## Layer 1 — Requirements (What)

Describe what this directive must accomplish. List functional and non-functional
requirements, acceptance criteria, or goals.

- [ ] _Requirement 1_
- [ ] _Requirement 2_
- [ ] _Requirement 3_

---

## Layer 2 — Orchestration (Decide)

Claude's decision-making guide for this directive. Describes how the parts work
together, the sequencing of steps, dependencies, and how to handle edge cases.
Claude reads this section to understand what to do and in what order.

### Steps

1. _Step 1 — description_
2. _Step 2 — description_
3. _Step 3 — description_

### Dependencies

- **Requires:** _list other directives or resources this one depends on_
- **Produces:** _list outputs consumed by other directives or systems_

### Edge Cases

_Document known failure modes, API limits, timing constraints, and how to handle them._

---

## Layer 3 — Execution (Do)

Deterministic scripts that perform the actual work. Claude checks this section
before writing any new code — existing scripts must be reused and improved, not duplicated.

### Environment Variables

List all required `.env` variables this directive depends on:

| Variable | Purpose |
|---|---|
| _VAR_NAME_ | _what it is used for_ |

### Scripts

| Script | Purpose | Status |
|---|---|---|
| _script-name.sh_ | _what it does_ | 🔴 Not created |

```bash
# Entry point to run this directive
# .claude/discover-directive/scripts/run.sh
```

---

## Deliverables

All outputs produced by this directive must be listed here with their destination.
Intermediates go in `.tmp/` and are never committed. Deliverables are final outputs.

| Deliverable | Type | Destination | Notes |
|---|---|---|---|
| _name_ | Local / Cloud / Both | _path or service URL_ | _format, access details_ |

> **Rule:** Local files are for processing only. If a deliverable lives in a cloud
> service, document the exact location so any session can find it without asking.

---

## Context

Running context, decisions made, and evolving understanding of this directive.
Updated as work progresses. Never overwritten without explicit user instruction.

### Decisions Log

| Date | Decision | Reason |
|---|---|---|
| _YYYY-MM-DD_ | _decision_ | _why_ |

### Self-Anneal Log

Record of every break-fix cycle. Each entry makes this directive stronger.

| Date | What broke | Root cause | Fix applied | Script updated? |
|---|---|---|---|---|
| _YYYY-MM-DD_ | _description_ | _cause_ | _what was changed_ | Yes / No |

### Open Questions

- _Question 1_

### Notes

_Any other context Claude or team members should know._
