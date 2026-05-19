---
name: connector-dialogue-doctrine-fold
description: >-
  Folds synthesis connector work into doctrine: connector → doctrine → handoff loop using
  docs/CONNECTOR_DIALOGUE_THREAD.md and PRODUCT_DOCTRINE. Use when editing
  synthesis connector entries, canonical drug/evidence work, or folding durable
  behavior into docs/AGENT_HANDOFF.md and changelog sections.
skill_category: product_pack
skill_pack: "[synthesis.]"
disable-model-invocation: true
---

# Fold synthesis connector into doctrine

## What this unlocks

Keeps **connector work from becoming orphan chat**: a fold-up checklist from thread entries into product doctrine, handoff, and acceptance scenarios when behavior changes.

## Origin in the [PWR] ecosystem

**[synthesis.]** repo-local connector discipline using `CONNECTOR_DIALOGUE_THREAD` and `PRODUCT_DOCTRINE` alongside scientific tooling skills.

## Broader applications

- Research software teams mixing fast iteration with evidence-bound product promises.
- Any org running ToolUniverse-scale retrieval beside changelogged doctrine.
- Program offices that need an explicit “thread → spec → tests” bridge.

## When to use

- Appending or closing **`docs/CONNECTOR_DIALOGUE_THREAD.md`** entries for **[synthesis.]**.
- Verifying that **schema / ingest / eval** plans in the thread were mirrored into **`docs/PRODUCT_DOCTRINE.md`** and **`docs/AGENT_HANDOFF.md`**.

## Repo anchors

- **Connector:** `docs/CONNECTOR_DIALOGUE_THREAD.md` — same append discipline as other PWR repos (Notes above **Running dialogue**; newest at end).
- **Doctrine:** `docs/PRODUCT_DOCTRINE.md` — evidence boundary, product thesis, §8 changelog when present.
- **Handoff:** `docs/AGENT_HANDOFF.md` — fragile modules, scripts, migration notes.

## Relationship to ToolUniverse

This repo also ships many **`tooluniverse-*`** skills for scientific tooling. **Governance** (connector + doctrine) answers *what the product promises and how we change it safely*; **ToolUniverse** answers *how to route scientific asks*. Do not let router behavior replace changelogged doctrine.

## Fold-up checklist

1. Connector heading status → **`DONE`** / **`BLOCKED`** when the slice of work is closed.
2. **PRODUCT_DOCTRINE** snapshot or narrative updated if operator-visible behavior changed.
3. **AGENT_HANDOFF** updated if commands, env, or fragile paths changed.
4. If a new **acceptance bar** exists, add or adjust **`handoff/CANONICAL_QUERIES.md`** (or repo equivalent).

## Cross-skill

- **`align-cross-repo-doctrine-connector-handoff`** — map across all PWR sibling repos.
- **`doctrine-vs-retrieval-arbitration`** — when to lean on product doctrine vs ToolUniverse router.

