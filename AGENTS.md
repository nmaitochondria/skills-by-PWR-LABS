# Agents working in **[skills.]** by **[PWR] LABS**

This repo is the **public** home for the skills **catalog**, **Notion playbook**, and **vendored `skills/<skill_id>/` packs**.

## Do

- Edit [`docs/SKILLS_PUBLICATION_CATALOG.md`](docs/SKILLS_PUBLICATION_CATALOG.md), [`docs/SKILLS_NOTION_HUB_PLAYBOOK.md`](docs/SKILLS_NOTION_HUB_PLAYBOOK.md), and refresh packs under [`skills/`](skills/) in **this** checkout.
- When describing public `SKILL.md` links, use:  
  `https://raw.githubusercontent.com/nmaitochondria/skills-by-PWR-LABS/main/skills/<skill_id>/SKILL.md`
- Keep catalog tables aligned with **`SKILL_ROWS`** in nucleus [`scripts/seed_pwr_skills_notion_pages.py`](https://github.com/PWR-LABS/nucleus/blob/main/scripts/seed_pwr_skills_notion_pages.py).
- After editing a pack, **push this repo** so GitHub and the landing site stay public.

## Do not

- Assume every row’s **Authoring repo** equals the Notion **`[product.]`** tag (see catalog note under **`[chaperone.]`**).
- Store **`SKILL_ROWS`**, Notion seed scripts, or **`NOTION_PWR_LABS_TOKEN`** here — they stay in **nucleus** for operator automation only.

## Nucleus (operator only)

Run hub sync from nucleus: `bash scripts/run_portfolio_notion.sh skills-hub`. The seed reads packs from the sibling checkout **`../skills by PWR LABS/skills/`** when present.
