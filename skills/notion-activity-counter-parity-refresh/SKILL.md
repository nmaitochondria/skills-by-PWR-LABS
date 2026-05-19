---
name: notion-activity-counter-parity-refresh
description: >-
  Refreshes AMCAS activity word/character trackers for student review hubs: canonical narrative
  inside toggles, "refresh word count" to-do, --rewrite-layout rebuild via build_activity_body,
  and sync_materials_templates --counter-parity for templates + PS + all known DBs. Use
  scripts/refresh_activity_counts.py from chaperone. Pair with structured-gdoc-notion-application-ingest.
skill_category: product_pack
skill_pack: "[chaperone.]"
# Commands and paths are relative to **chaperone** repo root.
disable-model-invocation: true
---

# Refresh chaperone activity Notion counts

**Scope:** Run from **[chaperone](https://github.com/nmaitochondria/chaperone)** repo root. Requires **`NOTION_CHAPERONE_TOKEN`** in **`chaperone/.env`** (same token story as **`structured-gdoc-notion-application-ingest`**). Uses **`notion_client`** and imports **`build_activity_body`**, batch append/delete helpers from **`scripts/import_activities_from_google_doc.py`**.

## Operator intent: review hubs

Badri/Paige **document-review** and **application-tracker** databases are the **review hubs** with students; stamped word/character lines and the refresh to-do are part of the coaching UX. **`sync_materials_templates.py --apply --counter-parity`** keeps **materials templates**, **both students’ PS material pages**, **tracker backfill from document-review when a tracker body is empty**, and **rewrite-layout** on all known activity DBs aligned after layout or counter changes.

## Keep skills in sync (agents)

Whenever you change **`scripts/refresh_activity_counts.py`**, **`scripts/import_activities_from_google_doc.py`**, **`scripts/sync_materials_templates.py`**, or **`../structured-gdoc-notion-application-ingest/references/notion-block-layout.md`**, update **this skill** and **[structured-gdoc-notion-application-ingest](../structured-gdoc-notion-application-ingest/SKILL.md)** together (and **`chaperone/.cursor/rules/notion-structure-sync.mdc`** when operator commands change).

## What gets counted (“selection”)

The script does **not** read arbitrary highlighted text from a browser. It recomputes metrics from the **same canonical narrative “selection”** the ingest layout uses:

| Region | Source in Notion | Limits echoed in layout |
| --- | --- | --- |
| **Experience description** | Text under the toggleable **`Experience description`** heading (paragraphs inside the toggle, plus non-noise paragraphs in that section) | **700** characters (limit line `word / character limit: 700 characters`; only the **character** ratio is green/red) |
| **Most meaningful** | Text under **`Most meaningful remarks`** (toggle body + following paragraphs in MM mode) | **1325** characters (same pattern) |

`_extract_sections` in **`refresh_activity_counts.py`** walks those headings; noise lines (`character limit:`, `current word count:`, `current character count:`, stub NA text, etc.) are excluded so counts reflect **story prose only**.

**Word count** = regex word tokens on that extracted text. When **`build_activity_body`** rebuilds counter lines, **green/red** applies only to the metric named on the **`word / character limit:`** line (`… characters` → colored char ratio; `… words` → colored word ratio). The other line is a **natural decimal count only** (no `/limit`, no color). There is no Notion-native “toggle” between modes—change the limit line and **`--rewrite-layout`**, or adjust code constants (e.g. secondary **`DEFAULT_SECONDARY_WORD_LIMIT`**).

## Refresh toggle mechanism

Ingest / layout code (**`import_activities_from_google_doc.build_activity_body`** → **`_counter_controls`**) stamps each section with:

1. A **`word / character limit: …`** line whose trailing unit (`characters` vs `words`) selects which of the two counters gets a green/red **`cur/limit`** ratio  
2. **`current word count:`** and **`current character count:`** paragraphs (one ratio-colored, one count-only per the limit line)  
3. A **`to_do`** block whose visible text is exactly **`refresh word count`** (unchecked by default)

**Operator workflow:** check **`refresh word count`** on an activity page when counts should be recomputed from the live body.

**Automation:** run **`refresh_activity_counts.py`** with **`--triggered-only`**. The script visits only rows whose page contains a checked **`refresh word count`** to-do, then:

- **Without `--rewrite-layout`:** extracts the selection above, **prints** `desc_chars`, `desc_words`, `mm_chars`, `mm_words` to stdout, and **unchecks** the to-do via the Notion API (`_reset_refresh_todos`). It does **not** update the counter paragraphs in the page.
- **With `--rewrite-layout`:** same extraction, then **replaces the entire page body** with a fresh **`build_activity_body(desc, mm)`** so **`current word count:`** / **`current character count:`** lines (including **Notion text colors** on the ratios) match the extracted selection; then unchecks the to-do. Use **`--all-known`** to refresh Badri tracker, Badri document-review, and Paige document-review in one pass when layout code changed.

A Notion **button** cannot call local Python; it can only flip state the script later reads (e.g. checking this to-do), matching the pattern in **`structured-gdoc-notion-application-ingest`**.

## What this unlocks

Keeps **word and character limits honest** for structured narrative blocks: re-derive text from Notion, expose a refresh toggle, and optionally rebuild canonical counter layouts from extracted “selection” text.

## Origin in the [PWR] LABS ecosystem

**[chaperone.]** activity pages: pairs with **`structured-gdoc-notion-application-ingest`** and **`scripts/refresh_activity_counts.py`** for description + most-meaningful sections and the **`refresh word count`** to-do gate.

## Broader applications

- Any form-driven narrative where UI counters drift from underlying text.
- Compliance-ish writing workflows with explicit limits (grants, character-capped bios).
- Teaching assistants how to separate “operator flipped a toggle” from “script recomputed truth.”

## When to use

- Operator flipped **`refresh word count`** and wants a **batch pass** over a database (`--triggered-only`).
- You need **stdout audit** of counts vs limits before trusting what Notion shows (`--triggered-only` optional; omit to process every row).
- Operator wants **counter lines on the page** to match extracted prose — **`--rewrite-layout`** (destructive full-body replace under that row’s page).

## Commands

From **chaperone** root (adjust venv path):

```bash
.venv/bin/python scripts/refresh_activity_counts.py --database-id <notion-db-id>
```

Process every row in one or more databases:

```bash
.venv/bin/python scripts/refresh_activity_counts.py --database-id <id-1> --database-id <id-2>
```

Built-in Badri/Paige document-review database ids (see script `KNOWN_DATABASES`):

```bash
.venv/bin/python scripts/refresh_activity_counts.py --all-known
```

**Triggered only** (pages where a to-do titled exactly `refresh word count` is checked):

```bash
.venv/bin/python scripts/refresh_activity_counts.py --database-id <id> --triggered-only
```

**Rewrite layout** (delete all block children under each row’s page, then append blocks from `build_activity_body`):

```bash
.venv/bin/python scripts/refresh_activity_counts.py --database-id <id> --rewrite-layout
```

To align **templates + both students’ PS material pages + all three known activity databases** in one command (from chaperone root):

```bash
.venv/bin/python scripts/sync_materials_templates.py --apply --counter-parity
```

That script also **fills empty Badri application-tracker activity bodies** from the **document-review** row with the same title (e.g. after a tracker row lost blocks) before rewriting layouts.

Without **`--rewrite-layout`**, the script does **not** rewrite `current word count:` / `current character count:` lines in place — it **prints** metrics and clears the refresh to-do. Use **`--rewrite-layout`** when the body should be regenerated from extracted text (read `refresh_activity_counts.py` before advising destructive flags).

## Surface discovery

Use **`scripts/inspect_badri_notion.py`** when you need a printed tree of hub child databases, Badri-titled rows, and nested **`child_database`** blocks under student pages. It expects **`NOTION_CHAPERONE_TOKEN`** and **`NOTION_CHAPERONE_DATABASE_ID`**.

## Cross-skill

- **`structured-gdoc-notion-application-ingest`** — Google Doc → Notion row and initial **`build_activity_body`** scaffold (including **`refresh word count`** to-dos and counter lines); this skill **re-derives selection + counts** from the live page when prose edits drift from stamped counters.

## References

Layout and counter conventions overlap with **[notion-block-layout.md](../structured-gdoc-notion-application-ingest/references/notion-block-layout.md)**.

