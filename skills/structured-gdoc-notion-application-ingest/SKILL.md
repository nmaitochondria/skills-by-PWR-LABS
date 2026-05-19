---
name: structured-gdoc-notion-application-ingest
description: >-
  Ingests AMCAS-style activities from Google Docs into Notion for student **review hubs**
  (document-review + application-tracker surfaces): dry-run, schema ensure, page-body
  word/character tracker scaffolds. Use chaperone scripts/import_activities_from_google_doc.py
  when GDoc export text does not match Notion rows. Pair with notion-activity-counter-parity-refresh.
skill_category: product_pack
skill_pack: "[chaperone.]"
# Commands and paths are relative to **chaperone** repo root.
disable-model-invocation: true
---

# Ingest AMCAS Google Doc → Notion

## What this unlocks

Automates **structured ingest of long-form application prose** from a Google Doc export into Notion rows and child pages—with dry-run, schema ensure, and verification patterns so “rows populated” ≠ “bodies true”.

## Origin in the [PWR] LABS ecosystem

**[chaperone.]** lane: AMCAS-style activities/experiences for graduate medical admissions workflows. This `SKILL.md` lives in the **chaperone** checkout beside **`scripts/`** and **`.cursor/rules/`** it references.

## Broader applications

- Any admissions or fellowship program importing narrative tables from Google Docs to a database.
- Grant or scholarship pipelines with similar “label + body” parsing hazards.
- Operator teams needing ingest discipline (dry-run first, verify child blocks) beyond med admissions.

**Scope:** Run all commands from the **[chaperone](https://github.com/nmaitochondria/chaperone)** repository root. Paths below are relative to that checkout. *Legacy Codex mirror id:* `chaperone-gdocs-notion-ingest`.

## Operator intent: review hubs

These ingests feed **live review with students** in Notion: each advisee’s **activities + experiences** (and related **application tracker** copy) is a working surface where **`word / character limit:`**, **`current word count`**, **`current character count`**, and the **`refresh word count`** to-do stay authoritative. The **materials** database is the template source for PS/secondary/activities for future students (`sync_materials_templates.py`). Treat counter/layout regressions as product bugs—fix code, then **`--counter-parity`** (see refresh skill).

## Keep skills in sync (agents)

Whenever you change **`scripts/import_activities_from_google_doc.py`**, **`scripts/refresh_activity_counts.py`**, **`scripts/sync_materials_templates.py`**, or **`references/notion-block-layout.md`**, update **this skill** and **[notion-activity-counter-parity-refresh](../notion-activity-counter-parity-refresh/SKILL.md)** in the **same** change (plus **`chaperone/.cursor/rules/notion-structure-sync.mdc`** when workflow flags change) so the story stays one source of truth.

## Workflow

1. Read `docs/CONNECTOR_DIALOGUE_THREAD.md` from the bottom and follow the newest open directive. Preserve append-only thread updates.
2. Confirm the target Notion surface before writing. Traverse from `NOTION_CHAPERONE_DATABASE_ID` with `NOTION_CHAPERONE_TOKEN`, then identify the student row, nested document-review/materials databases, and any application-tracker database the operator is actually viewing.
3. Dry-run the Google Doc parse before any live write. Use `--dry-run` and check row count plus `desc_len` and `mm_len`; do not trust row count alone.
4. Write only after the target surface is clear. Use `--ensure-schema` for simple target databases whose title property is `Name` and whose activity columns are missing.
5. Verify live Notion at three levels: database row count, key properties, and child page body content under counters/dividers. A page with scaffold blocks and `current character count: 000/700` is not populated.
6. After changing **block layout or counter presentation** in `scripts/import_activities_from_google_doc.py`, push to Notion before signing off: run **`scripts/sync_materials_templates.py --apply --counter-parity`** (templates + Badri & Paige PS material pages + all known activity DBs with **`--rewrite-layout`**), or narrower flags as needed. Canonical materials DB: `https://www.notion.so/35d50bc77832808591cbd498254d55b7?v=35d50bc77832805196bf000c41fd4635`. See **`chaperone/.cursor/rules/notion-structure-sync.mdc`**.
7. Append a concise connector-thread note with exact database IDs, commands or command shapes, row counts, `missing_desc`, `mm_rows`, and any source-doc oddities.

## Chaperone commands

Prefer repo-local Python from **chaperone** root:

```bash
.venv/bin/python scripts/import_activities_from_google_doc.py \
  --database-id <notion-db-id> \
  --doc-url '<google-doc-export-format-txt-url>' \
  --format original_tabular \
  --dry-run
```

For Badri-style target databases that only have `Name` initially:

```bash
.venv/bin/python scripts/import_activities_from_google_doc.py \
  --database-id <target-db-id> \
  --doc-url '<google-doc-export-format-txt-url>' \
  --format original_tabular \
  --ensure-schema
```

Use `scripts/inspect_badri_notion.py` when diagnosing Badri’s surfaces. Extend it or write a narrow one-off query when a different student is involved.

## Known failure modes

- Google Doc text export may put the `Description` label on a tab-indented line and the actual description text on unindented lines. The parser must treat those unindented narrative lines as body text until the next real activity title followed by `Dates`.
- Notion row properties can be populated while page bodies are blank. Always inspect child blocks and counters.
- There can be multiple `activities + experiences` databases with identical schemas. Do not assume the imported DB is the operator-visible table.
- Notion API does not support all block types. Native Notion button blocks are returned as `unsupported` with `unsupported.block_type` such as `button`; do not build workflows that require creating or reading button internals through the API.
- Date oddities can originate in the source doc. Report them rather than silently normalizing beyond the existing parser policy.

## Count refresh pattern

Prefer the bundled skill **[notion-activity-counter-parity-refresh](../notion-activity-counter-parity-refresh/SKILL.md)** and **`scripts/refresh_activity_counts.py`** rather than hand-editing counters in Notion.

If the user asks for character or word counts, use **`scripts/refresh_activity_counts.py`**: default mode extracts text and prints counts while clearing **`refresh word count`** to-dos; add **`--rewrite-layout`** when the operator wants the page body rebuilt so counters match code (green/red only on the metric named on the **`word / character limit:`** line—see refresh skill).

Use a to-do titled **`refresh word count`** as the API-visible trigger when the operator wants a button-like workflow (`--triggered-only`). A manually-created Notion button may set that checkbox, but the local script still has to run and consume it; the public API cannot make a button call local code by itself.

## References

Read [references/notion-block-layout.md](references/notion-block-layout.md) before modifying activity page body layouts or count-refresh behavior.

**Codex CLI (optional):** [references/codex-openai-interface.example.yaml](references/codex-openai-interface.example.yaml) — interface snippet for OpenAI Codex agent bundles; not used by Cursor.

