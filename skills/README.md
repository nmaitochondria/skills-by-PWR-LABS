# Public skill packs (`skills/<skill_id>/`)

Each subdirectory is a **full copy** of the corresponding Cursor Agent Skill from a sibling product repo, keyed by the **canonical skill id** in nucleus [`SKILL_ROWS`](https://github.com/PWR-LABS/nucleus/blob/main/scripts/seed_pwr_skills_notion_pages.py). Directory names match those ids (for example `portfolio-wide-governance` mirrors `.cursor/skills/nucleus-global-admin/` in nucleus).

**Why this lives here:** **[skills-by-PWR-LABS](https://github.com/nmaitochondria/skills-by-PWR-LABS)** is the **public** repo. Vendored trees stay in **this** checkout so anyone can browse, clone, and download `SKILL.md` without access to private product orgs or nucleus.

**Source of truth for authoring:** each product checkout’s `.cursor/skills/<folder>/`. After you edit a skill there, refresh the public pack:

```bash
# Example (adjust sibling path and skill id)
rsync -a ../ribosome/.cursor/skills/align-cross-repo-doctrine-connector-handoff/ \
  "./skills/align-cross-repo-doctrine-connector-handoff/"
```

**Catalog + Notion playbook:** [`docs/SKILLS_PUBLICATION_CATALOG.md`](../docs/SKILLS_PUBLICATION_CATALOG.md), [`docs/SKILLS_NOTION_HUB_PLAYBOOK.md`](../docs/SKILLS_NOTION_HUB_PLAYBOOK.md).

**Hub sync (operator):** still run from **[PWR-LABS/nucleus](https://github.com/PWR-LABS/nucleus)** — `bash scripts/run_portfolio_notion.sh skills-hub`. The seed script reads **`../skills by PWR LABS/skills/<skill_id>/SKILL.md`** when this sibling checkout is present.

**Raw download URL pattern:**

`https://raw.githubusercontent.com/nmaitochondria/skills-by-PWR-LABS/main/skills/<skill_id>/SKILL.md`
