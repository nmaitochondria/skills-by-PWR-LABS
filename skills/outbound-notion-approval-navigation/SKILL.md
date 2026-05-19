---
name: outbound-notion-approval-navigation
description: >-
  Navigates Atherton Notion approval surfaces: Draft Message, Edited Message,
  Outreach message type, optional Call Prep / Edited Call Prep, pipeline columns vs Apollo
  typed_custom_fields. Points to PROSPECTING_SKILL.md as canonical operational narrative.
skill_category: product_pack
skill_pack: "[ribosomal.]"
disable-model-invocation: true
---

# Navigate outbound Notion approval

## What this unlocks

Maps **where approved copy lives vs automation truth** in Notion: draft vs edited columns, message types, and optional call-prep surfaces—so humans know what they own after sync.

## Origin in the [PWR] ecosystem

**[ribosomal.]** approval layout aligned with **`PROSPECTING_SKILL.md`** narrative; executable mirror rules remain in ribosome when adopted.

## Broader applications

- Any bi-directional CRM ↔ workspace layout with human-in-the-loop approval columns.
- Playbooks for SDR teams learning which fields must never be overwritten by robots.
- Documentation patterns for “navigator” pages separate from long operational manuals.

## When to use

- Explaining **where** approved copy lives vs **Apollo sequence truth**.
- Aligning **`--discover`** pipeline option lists with **Message Outreach** / **Call Outreach** columns.

## Core layout (Coral-style)

- **`Draft Message`** — unified working column mirrored from Apollo **`typed_custom_fields`** (LinkedIn → email 1 → email 2 precedence per upstream ribosome policy **when adopted here**).
- **`Edited Message`** — human-approved copy; **ribosome does not overwrite** this column.
- **`Outreach message type`** — select/status aligned with prospecting skill layouts (A/B/C) when configured.
- **Layout B (optional):** **`Call Prep`** from Apollo **`ai_call_note`**; **`Edited Call Prep`** for human edits — same non-overwrite discipline for edited columns.

## Canonical narrative (do not duplicate here)

- **`PROSPECTING_SKILL.md`** — end-to-end operational workflow: research cadence, Perplexity usage, Notion approval loop, PATCH semantics philosophy.
- This skill is a **map**, not a replacement for that document.

## Upstream behavior

Executable mirror rules live in **`ribosome`**; **ribosomal** doctrine **§0.2** + **`.env.example`** say which upstream features this lane **adopts**.

## Cross-skill

- **`apollo-notion-outbound-preflight`** — validate schema before trusting sync output.
- **`outbound-vs-central-executor-scope`** — executor vs lane ownership.

