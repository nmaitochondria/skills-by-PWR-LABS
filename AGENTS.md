# Agents working in **[skills.]** by **[PWR] LABS**

This repo is **public documentation only** (catalog + Notion playbook). Treat it as the **reader-facing** source of truth for those Markdown files.

## Do

- Edit [`docs/SKILLS_PUBLICATION_CATALOG.md`](docs/SKILLS_PUBLICATION_CATALOG.md) and [`docs/SKILLS_NOTION_HUB_PLAYBOOK.md`](docs/SKILLS_NOTION_HUB_PLAYBOOK.md) here; use **full GitHub URLs** when linking to **PWR-LABS/nucleus** `skills/` or scripts (this checkout may not contain those trees).
- When describing “public” `SKILL.md` links, use the **nucleus** raw pattern already in the catalog:  
  `https://raw.githubusercontent.com/PWR-LABS/nucleus/main/skills/<skill_id>/SKILL.md`
- Keep catalog tables aligned with **`SKILL_ROWS`** in nucleus [`scripts/seed_pwr_skills_notion_pages.py`](https://github.com/PWR-LABS/nucleus/blob/main/scripts/seed_pwr_skills_notion_pages.py).

## Do not

- Assume every row’s **Authoring repo** equals the Notion **`[product.]`** tag. They differ when a skill is **tagged** one way in Notion but **authored** from another checkout (see the note under **`[chaperone.]`** in the catalog).
- Move **`SKILL_ROWS`**, the Notion seed, or **`NOTION_PWR_LABS_TOKEN`** workflows into this repo — they belong in **nucleus** so secrets and automation stay in one place.

## Opinion (architecture)

Having agents “resolve everything to this repo” for **execution** (sync, vendored trees, seed) would duplicate logic and secrets; you would fight drift. This repo is the right place for **focused doc + index** responsibility; nucleus remains the **operator** surface for packs + hub sync.
