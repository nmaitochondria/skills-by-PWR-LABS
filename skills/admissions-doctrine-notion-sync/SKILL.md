---
name: admissions-doctrine-notion-sync
description: >-
  Syncs chaperone product doctrine from git to Notion via scripts/sync_doctrine_to_notion.sh
  (CHAPERONE_DOCTRINE_NOTION_SOURCE.md, NOTION_DOCTRINE_SYNC.md). Use when editing chaperone Notion-facing doctrine or
  debugging pink inline-code accents and managed-body boundaries.
skill_category: product_pack
skill_pack: "[chaperone.]"
disable-model-invocation: true
---

# Sync chaperone doctrine to Notion

## What this unlocks

Publishes **product doctrine from git to a live Notion reading surface** with managed-body boundaries, pink inline accents, and a repeatable sync command—so doctrine is browsable without opening the repo.

## Origin

**[chaperone.]** publishes doctrine with **`bash scripts/sync_doctrine_to_notion.sh`** (loads **`NOTION_CHAPERONE_TOKEN`**) and **`NOTION_CHAPERONE_DOCTRINE_PAGE_ID`** (defaults in the script). The shell script runs **`scripts/sync_chaperone_doctrine_page.py --notion-sync-chaperone-product-doctrine`** in this checkout.

## Broader applications

- Any small product team mirroring Markdown doctrine to Notion for stakeholders.
- Programs where brand-colored inline code improves scanability for operators.
- Multi-repo foundries that want one sync tool across products.

## When to use

- Changing **`docs/CHAPERONE_DOCTRINE_NOTION_SOURCE.md`** or **`docs/NOTION_DOCTRINE_SYNC.md`**.
- Explaining how **[chaperone.]** doctrine reaches the live Notion page.

## Contract

| Piece | Role |
| --- | --- |
| **`NOTION_CHAPERONE_TOKEN`** | **[chaperone.]** Notion internal integration (doctrine + hub + connector scripts). |
| **`NOTION_CHAPERONE_DOCTRINE_PAGE_ID`** | Target Notion page (optional in **`.env`** — **`sync_doctrine_to_notion.sh`** has a canonical default). |
| **`docs/CHAPERONE_DOCTRINE_NOTION_SOURCE.md`** | Managed Markdown body (e.g. images under **`docs/assets/`** relative to this repo). |
| **`scripts/sync_doctrine_to_notion.sh`** *(chaperone)* | Operator entrypoint; sources **`.env`**, then runs **`scripts/sync_chaperone_doctrine_page.py`**. |

## Commands (from chaperone checkout)

```bash
cd /path/to/chaperone
bash scripts/sync_doctrine_to_notion.sh
# optional: --dry-run as first argument
```

See **`docs/NOTION_DOCTRINE_SYNC.md`** in **chaperone** for page title conventions and manual vs managed zones.

## Boundaries

- **Small** Markdown edits → run **`sync_doctrine_to_notion.sh`** after change; **large** structural edits → confirm with operator before live sync (**`docs/NOTION_DOCTRINE_SYNC.md`**).

## Cross-skill

- Other **[chaperone.]** skills in **`.cursor/skills/README.md`** (materials, cadence, integrity).

