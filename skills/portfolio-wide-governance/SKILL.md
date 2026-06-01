---
name: portfolio-wide-governance
description: >-
  PWR LABS portfolio admin: investor narrative baseline, public skills catalog (GitHub + chromosomes),
  design language v1 (inherited from ribosome), governance, and cross-repo publication
  coordination. Use in the nucleus repo or when explicitly tasked as global admin.
skill_category: governance
disable-model-invocation: true
---

# [nucleus.] global admin

## When to use

- Coordinating **Product Preview**, **[skills.]** public docs on GitHub ([catalog](https://github.com/nmaitochondria/skills-by-PWR-LABS/blob/main/docs/SKILLS_PUBLICATION_CATALOG.md), [playbook](https://github.com/nmaitochondria/skills-by-PWR-LABS/blob/main/docs/SKILLS_PUBLICATION_PLAYBOOK.md)), live site **[pwr-labs.ai/chromosomes](https://pwr-labs.ai/chromosomes)**, and nucleus [`skills/`](../../skills/) pointer docs.
- Updating **design language baseline** after founder decisions (`docs/NUCLEUS_DESIGN_LANGUAGE_BASELINE.md`).
- Auditing sibling repos for **new public skills** or **publication drift**.
- Routing **Codex** / repo agents so portfolio work lands in **nucleus** `CONNECTOR_DIALOGUE_THREAD`, not only ribosome.

## Operating spine (read first)

1. [`docs/NOTION_DOCTRINE_SYNC_OWNERSHIP.md`](../../docs/NOTION_DOCTRINE_SYNC_OWNERSHIP.md) — **`NOTION_PWR_LABS_TOKEN`** for portfolio surfaces (investor, My Notion AI, nucleus doctrine); **`NOTION_NUCLEUS_TOKEN`** is a deprecated alias; **`NOTION_<PRODUCT>_TOKEN`** + repo-local hooks for product lanes
2. [`docs/NUCLEUS_CONNECTOR_ENV.md`](../../docs/NUCLEUS_CONNECTOR_ENV.md)
3. [`docs/PRODUCT_DOCTRINE.md`](../../docs/PRODUCT_DOCTRINE.md)
4. [`docs/NUCLEUS_INTERFACES.md`](../../docs/NUCLEUS_INTERFACES.md)
5. [`docs/NUCLEUS_PUBLICATION_PLAYBOOK.md`](../../docs/NUCLEUS_PUBLICATION_PLAYBOOK.md)
6. [`docs/NUCLEUS_GOVERNANCE.md`](../../docs/NUCLEUS_GOVERNANCE.md)
7. [`docs/CONNECTOR_DIALOGUE_THREAD.md`](../../docs/CONNECTOR_DIALOGUE_THREAD.md)

## Implementation

- **When the user says “refresh the skills catalog”** (or equivalent): update **`SKILL_ROWS`** + public **[skills.]** catalog in **skills-by-PWR-LABS**, push GitHub, verify [pwr-labs.ai/chromosomes](https://pwr-labs.ai/chromosomes). **Do not** run Notion skills-hub sync unless explicitly reviving the archived hub.
- **Investor + portfolio Notion** commands: run **from nucleus** (`bash scripts/run_portfolio_notion.sh investor …` / `notion-ai` / `nucleus-doctrine` per the publication playbook). Set **`NOTION_PWR_LABS_TOKEN`** in **`nucleus/.env`** — the legacy **`NOTION_TOKEN`** name is **not** read (no fallbacks).
- **Per-product doctrine pages:** each sibling repo runs its **own** sync with **`NOTION_<PRODUCT>_TOKEN`** — never reuse portfolio **`NOTION_PWR_LABS_TOKEN`** for those pages (see ownership doc above).
