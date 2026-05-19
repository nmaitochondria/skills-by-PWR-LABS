---
name: align-cross-repo-doctrine-connector-handoff
description: >-
  Maps the shared **[PWR]** documentation loop across repos: PRODUCT_DOCTRINE,
  CONNECTOR_DIALOGUE_THREAD, AGENT_HANDOFF, optional NOTION_*_DOCTRINE_SYNC and
  CANONICAL_QUERIES. Use when bootstrapping a sibling repo, auditing handoff completeness,
  or explaining how connector directives fold into durable git truth.
skill_category: governance
# Notion: tag **Governance** only — no `[product.]` pack (shared across repos).
disable-model-invocation: true
---

# Map doctrine loop (cross-repo)

## What this unlocks

Gives any multi-repo organization a **single mental map** for how durable truth moves: from working dialogue, into operator-facing doctrine, into engineering handoff and acceptance checks. It prevents “we shipped it in chat” drift by naming the artifacts and the fold-up rule explicitly.

## Origin in the [PWR] ecosystem

**[PWR] LABS** standardizes the same loop across **[ribosome.]**, **[golgi.]**, **[synthesis.]**, **[chaperone.]**, and **[ribosomal.]**: `PRODUCT_DOCTRINE`, `CONNECTOR_DIALOGUE_THREAD`, `AGENT_HANDOFF`, optional Notion sync docs, and canonical scenarios when the bar moves.

## Broader applications

- Onboarding engineers and PMs onto a repo with a predictable documentation spine.
- Auditing whether a connector directive was fully handed off (not only merged in code).
- Explaining to investors or partners how governance stays coherent across a portfolio of products.
- Forking the pattern into any team that uses Git + Markdown as source of truth beside Notion or Linear.

## When to use

- Standing up **golgi**, **synthesis**, **chaperone**, **ribosomal**, or **ribosome** with the same **connector → doctrine → handoff** discipline.
- Checking whether a connector directive was **fully handed off** (not only implemented in code).

## Shared pattern

| Artifact | Role |
| --- | --- |
| **`docs/PRODUCT_DOCTRINE.md`** | Operator story + **codebook** + dated **§8 changelog** when present. |
| **`docs/CONNECTOR_DIALOGUE_THREAD.md`** | Append-only **Running dialogue**; two-layer directives (plain language + technical contract). |
| **`docs/AGENT_HANDOFF.md`** | Engineering fragility, commands, env caveats — **not** product philosophy. |
| **`docs/NOTION_*_DOCTRINE_SYNC.md`** *(optional)* | Notion managed-body boundary + page ids (where the repo syncs doctrine). |
| **`handoff/CANONICAL_QUERIES.md`** *(when used)* | Copy/paste acceptance scenarios when the bar moves. |

## Per-repo paths (sibling checkouts)

| Repo | Doctrine | Connector | Handoff | Notion sync doc |
| --- | --- | --- | --- | --- |
| **ribosome** | `docs/PRODUCT_DOCTRINE.md` | `docs/CONNECTOR_DIALOGUE_THREAD.md` | `docs/AGENT_HANDOFF.md` | `docs/NOTION_PRODUCT_DOCTRINE_SYNC.md` |
| **golgi** | `docs/PRODUCT_DOCTRINE.md` | `docs/CONNECTOR_DIALOGUE_THREAD.md` | `docs/AGENT_HANDOFF.md` | `docs/NOTION_DOCTRINE_SYNC.md` |
| **synthesis** | `docs/PRODUCT_DOCTRINE.md` | `docs/CONNECTOR_DIALOGUE_THREAD.md` | `docs/AGENT_HANDOFF.md` | `docs/NOTION_DOCTRINE_SYNC.md` |
| **chaperone** | `docs/PRODUCT_DOCTRINE.md` | `docs/CONNECTOR_DIALOGUE_THREAD.md` | `docs/AGENT_HANDOFF.md` | `docs/NOTION_DOCTRINE_SYNC.md` |
| **ribosomal** | `docs/PRODUCT_DOCTRINE.md` | *(connector in ribosome optional)* | `docs/AGENT_HANDOFF.md` | Lane contract in doctrine §0.2 |

**Ribosomal nuance:** lane **contracts** live in **ribosomal** first; heavy **executor** behavior may live in **ribosome** — still fold durable truth back into ribosomal doctrine + canonical queries.

## Handoff rule

Closing a connector entry without updating the **doctrine / handoff / (metadata policy when applicable)** files is **incomplete** unless the user asked for a local-only experiment.

## Bundled skills

Use **`append-only-connector-directive-log`** for append-only log mechanics and connector writing standard detail.

