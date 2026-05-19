---
name: apollo-notion-outbound-preflight
description: >-
  Preflights Atherton outbound Apollo ↔ Notion: run-atherton-preflight, discover-only, daily Apollo sync
  with DRY_RUN rehearsals. Use before batch sync days or after Notion schema edits.
skill_category: product_pack
skill_pack: "[ribosomal.]"
disable-model-invocation: true
---

# Preflight outbound Apollo ↔ Notion

## What this unlocks

Provides **preflight + rehearsal scripts** for outbound sync: schema discovery, dry-run sequences, and operator tasks so batch days do not surprise the database.

## Origin in the [PWR] ecosystem

**[ribosomal.]** scripts (`run-atherton-preflight.sh`, discover-only, daily sync) invoking ribosome from the correct cwd with ribosomal `.env`.

## Broader applications

- Any Apollo-class ↔ Notion integration with operator-run scripts instead of hosted SaaS.
- Sales ops teams adopting “discover after schema churn” as mandatory ritual.
- Multi-sequence outbound stacks needing DRY_RUN rehearsal discipline.

## When to use

- **Aviation-style** “checks before you rely on the lane” — schema sanity, provision dry-run, optional Apollo rehearsal.
- After **Notion column** or **pipeline option list** edits (always re-**`discover`**).

## From ribosomal repo root

```bash
./scripts/run-atherton-preflight.sh    # smoke + dry-run pieces
./scripts/run-daily-apollo-sync.sh     # live Apollo → Notion (per .env scout/sequences)
./scripts/run-discover.sh              # fastest: schema + pipelines only
```

**VS Code / Cursor:** **Run Task…** → **`ribosomal: preflight`**, **`ribosomal: sync now (daily)`**, **`ribosomal: discover only`** (see **`.vscode/tasks.json`**).

## macOS shortcuts

- **`scripts/ribosomal-preflight.command`** / **`ribosomal-sync-now.command`** — double-click Terminal runners after `chmod +x`.

## What preflight is **not**

- It does **not** replace scheduled daily sync; it tells you the lane looks **sane** before ingest or after schema churn.
- **`DRY_RUN=1`** sequence rehearsals **must** stay no-op on Notion when rehearsing destructive paths — follow **`run-sync-apollo-sequence-dry-run.sh`** discipline.

## Cross-skill

- **`outbound-vs-central-executor-scope`** — who owns contracts vs executor.
- **`outbound-notion-approval-navigation`** — what operators edit after sync lands.

