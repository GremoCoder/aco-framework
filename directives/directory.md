# Directory: directives/

## Purpose

Contains the directive definition file for each feature domain or workflow in this project.
Each `.md` file here is the human-readable specification for a directive — its purpose,
scope, and ownership.

Each definition file corresponds to a `{name}-directive/` workspace under `.claude/`
and is created automatically when you run `/setup {name}`.

## Framework SOPs (exportable)

| File | Domain |
|------|--------|
| `discover.md` | Azure infrastructure discovery |
| `finops.md` | FinOps cost management and reporting |
| `assess.md` | Security assessment (WAF + HIPAA) |

## Client Overlays (client repo only — never exported)

| File | Contents |
|------|---------|
| `discover.client.md` | Subscriptions, flat-architecture notes, known SKIPPED queries |
| `finops.client.md` | Subscriptions, resource groups, tag values, budgets, cost baseline |
| `assess.client.md` | Engagement context — platform, services, Azure environment, risks |

> **Convention:** Each `{name}.client.md` is the client overlay for `{name}.md`. It contains
> only client-specific context — no SOP steps or framework content. When the client environment
> changes, update the `.client.md` file; the parent directive stays unchanged.
> `.client.md` files are never exported to aco-framework.

## Guidelines

- One framework SOP per directive — named `{name}.md`. The single source of truth for spec, orchestration, execution, and self-anneal log. Never add client-specific data here.
- One client overlay per directive — named `{name}.client.md`. Created automatically by `/setup {name}`. Populate before running the directive for the first time.
- `.client.md` files hold client-specific context only — not SOP steps or framework logic.
- Never export `.client.md` files. They belong to the client repo only.
- The corresponding workspace lives at `.claude/{name}-directive/` — it does NOT contain a copy of the directive file.
- Always edit files here in `directives/`. Never duplicate them.
- To clear generated data (`.tmp/`, `logs/`, `reports/`) from a directive workspace, run `/clear-data {name}`.
