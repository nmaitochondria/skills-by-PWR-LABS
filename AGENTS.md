# AGENTS.md — [skills.] public repo

This repo is the **public** home for the skills **catalog**, **publication playbook**, and **vendored `skills/<skill_id>/` packs**.

## Canonical public surfaces

- **Site:** [pwr-labs.ai/chromosomes](https://pwr-labs.ai/chromosomes)
- **Catalog:** [`docs/SKILLS_PUBLICATION_CATALOG.md`](docs/SKILLS_PUBLICATION_CATALOG.md)
- **Packs:** [`skills/`](skills/)

The **Notion skills hub is retired** — do not link to it or run hub sync unless explicitly reviving it.

## When editing here

- Keep catalog tables aligned with **`SKILL_ROWS`** in nucleus [`scripts/seed_pwr_skills_notion_pages.py`](https://github.com/PWR-LABS/nucleus/blob/main/scripts/seed_pwr_skills_notion_pages.py) (audit parity only).
- Refresh **`skills/<skill_id>/`** from sibling product checkouts after authoring changes (see [`skills/README.md`](skills/README.md)).
- Follow [`docs/SKILLS_PUBLICATION_PLAYBOOK.md`](docs/SKILLS_PUBLICATION_PLAYBOOK.md).

## Do not

- Store **`NOTION_PWR_LABS_TOKEN`**, Notion seed scripts, or operator automation in this repo — those stay in **nucleus**.
- Point readers at the old Notion hub URL.
