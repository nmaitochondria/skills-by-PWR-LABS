---
name: cross-repo-edge-audit
description: >-
  Run a heuristic audit across PWR sibling checkouts for literal ../<repo>/ path edges in code,
  hooks, and workflows. Use under [PWR] LABS governance when converging scripts so repos stay
  independently clonable; pair with docs/CROSS_REPO_AND_NUCLEUS_RUNNER.md.
skill_category: governance
disable-model-invocation: true
---

# Cross-repo edge audit ([PWR] LABS governance)

## What this unlocks

A **repeatable, machine-readable sweep** for the most common accidental cross-checkout coupling: **hard-coded sibling relative paths** (`../ribosome/`, `../chaperone/`, …) inside **automation surfaces** (shell, Python, workflows). It does **not** build a full import graph; it is a **cheap tripwire** you can run before declaring a repo “standalone.”

## Origin

**[nucleus.]** ships **`scripts/audit_cross_repo_edges.py`**. Default **`--scope code`** only walks each repo’s **`scripts/`**, **`.githooks/`**, and **`.github/workflows/`** so prose in **`docs/`** does not drown the signal. Use **`--scope all`** for a noisier repo-wide pass (operator judgment).

## When to use

- After refactors that claim “no sibling checkout required.”
- Before adding CI that should fail when a new `../other-repo/` edge appears.
- When onboarding a new repo into the same **`PWR_CURSOR_ROOT`** layout.

## Commands (from nucleus checkout)

```bash
cd /path/to/nucleus
python3 scripts/audit_cross_repo_edges.py
python3 scripts/audit_cross_repo_edges.py --json
python3 scripts/audit_cross_repo_edges.py --strict --scope code
```

**Environment (optional):**

- **`PWR_CURSOR_ROOT`** — directory containing **`ribosome/`**, **`nucleus/`**, etc. (defaults to parent of nucleus).
- **`PWR_EDGE_AUDIT_REPOS`** — comma-separated repo folder names to scan.
- **`PWR_EDGE_AUDIT_SCOPE`** — `code` or `all` (overrides default when set).

**Notion + GitHub publication:** keep **`SKILL_ROWS`** and the public **[skills.]** catalog aligned (`docs/SKILLS_PUBLICATION_CATALOG.md` in **skills-by-PWR-LABS**); refresh **`skills/cross-repo-edge-audit/`** mirror on **PWR-LABS/nucleus**; public surface is [pwr-labs.ai/chromosomes](https://pwr-labs.ai/chromosomes) + GitHub — **not** the retired Notion skills hub.

## Boundaries

- **False positives:** intentional delegation (temporary) may still match; track with issues or remove literals by vendoring/packaging.
- **False negatives:** dynamic paths, env-only configuration, or SSH remotes are not analyzed here.
- **Secrets:** this script does **not** read `.env` contents; it scans **source text** only.

## Related docs

- **`docs/CROSS_REPO_AND_NUCLEUS_RUNNER.md`** — who may depend on whom.
- **`docs/NUCLEUS_PUBLICATION_PLAYBOOK.md`** — where portfolio commands run.
- **`scripts/audit_notion_doctrine.py`** — complementary Notion token + hook spot checks.
