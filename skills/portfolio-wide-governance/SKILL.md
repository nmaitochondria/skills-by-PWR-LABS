---
name: portfolio-wide-governance
description: >-
  PWR LABS portfolio admin: investor narrative baseline, public skills hub + mirror,
  design language v1 (inherited from ribosome), governance, and cross-repo publication
  coordination. Use in the nucleus repo or when explicitly tasked as global admin.
skill_category: governance
disable-model-invocation: true
---

# [nucleus.] global admin

## When to use

- Coordinating **Product Preview**, **[skills.]** public docs on GitHub ([catalog](https://github.com/nmaitochondria/skills-by-PWR-LABS/blob/main/docs/SKILLS_PUBLICATION_CATALOG.md), [playbook](https://github.com/nmaitochondria/skills-by-PWR-LABS/blob/main/docs/SKILLS_NOTION_HUB_PLAYBOOK.md)) plus **nucleus** vendored [`skills/`](../), and **Notion skills hub** from nucleus entrypoints.
- Updating **design language baseline** after founder decisions (`docs/NUCLEUS_DESIGN_LANGUAGE_BASELINE.md`).
- Auditing sibling repos for **new public skills** or **publication drift**.
- Routing **Codex** / repo agents so portfolio work lands in **nucleus** `CONNECTOR_DIALOGUE_THREAD`, not only ribosome.

## Operating spine (read first)

1. [`docs/NOTION_DOCTRINE_SYNC_OWNERSHIP.md`](../../docs/NOTION_DOCTRINE_SYNC_OWNERSHIP.md) — **`NOTION_PWR_LABS_TOKEN`** (investor / skills hub / portfolio), **`NOTION_NUCLEUS_TOKEN`** (operator doctrine page only), vs **`NOTION_<PRODUCT>_TOKEN`** + repo-local hooks
2. [`docs/NUCLEUS_CONNECTOR_ENV.md`](../../docs/NUCLEUS_CONNECTOR_ENV.md)
3. [`docs/PRODUCT_DOCTRINE.md`](../../docs/PRODUCT_DOCTRINE.md)
4. [`docs/NUCLEUS_INTERFACES.md`](../../docs/NUCLEUS_INTERFACES.md)
5. [`docs/NUCLEUS_PUBLICATION_PLAYBOOK.md`](../../docs/NUCLEUS_PUBLICATION_PLAYBOOK.md)
6. [`docs/NUCLEUS_GOVERNANCE.md`](../../docs/NUCLEUS_GOVERNANCE.md)
7. [`docs/CONNECTOR_DIALOGUE_THREAD.md`](../../docs/CONNECTOR_DIALOGUE_THREAD.md)

## Implementation

- **When the user says “sync the skills hub”** (or equivalent): from **nucleus** root run **`bash scripts/run_portfolio_notion.sh skills-hub`** (refreshes catalog row properties + bodies per playbook).
- **Investor + skills hub + public portfolio** commands: run **from nucleus** (`bash scripts/run_portfolio_notion.sh …` per the publication playbook). Set **`NOTION_PWR_LABS_TOKEN`** in **`nucleus/.env`** for investor and skills hub — the legacy **`NOTION_TOKEN`** name is **not** read (no fallbacks). The **[nucleus.]** operator doctrine Notion page uses **`NOTION_NUCLEUS_TOKEN`** + **`NOTION_NUCLEUS_DOCTRINE_PAGE_ID`** (`nucleus-doctrine` subcommand only).
- **Per-product doctrine pages:** each sibling repo runs its **own** sync with **`NOTION_<PRODUCT>_TOKEN`** — never reuse portfolio **`NOTION_PWR_LABS_TOKEN`** or **`NOTION_NUCLEUS_TOKEN`** for those pages (see ownership doc above).
