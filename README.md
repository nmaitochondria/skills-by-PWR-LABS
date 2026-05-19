# [skills.] by [PWR] LABS

Public home for **[skills.]**: the **catalog**, **Notion playbook**, and **downloadable skill packs** (`skills/<skill_id>/`) all live **in this repository**.

- **Notion hub:** [skills by PWR LABS](https://www.notion.so/skills-by-PWR-LABS-35d50bc778328020a178d10e7a091bee)
- **GitHub:** [nmaitochondria/skills-by-PWR-LABS](https://github.com/nmaitochondria/skills-by-PWR-LABS) — local checkout folder name may include spaces (`skills by PWR LABS`) beside **golgi**, **nucleus**, **ribosome**, etc.

**Operator automation** (Notion hub seed, portfolio token) still runs from **[PWR-LABS/nucleus](https://github.com/PWR-LABS/nucleus)** — see [`docs/NUCLEUS_PUBLICATION_PLAYBOOK.md`](https://github.com/PWR-LABS/nucleus/blob/main/docs/NUCLEUS_PUBLICATION_PLAYBOOK.md). Readers download packs from **this** repo; nucleus only executes sync.

---

## Git vs this repo

| Layer | Where it lives | What it is |
| --- | --- | --- |
| **Authoring** | Each product checkout (e.g. `ribosome/.cursor/skills/…`, `chaperone/.cursor/skills/…`, `nucleus/.cursor/skills/…`) | Canonical `SKILL.md` sources for Cursor and git history. |
| **Public packs** | **This repo [`skills/`](skills/)** | Full **per–skill-id** trees for public browse/clone/raw URLs. Refresh from sibling checkouts when skills change (see [`skills/README.md`](skills/README.md)). |
| **Machine list** | **[nucleus `scripts/seed_pwr_skills_notion_pages.py`](https://github.com/PWR-LABS/nucleus/blob/main/scripts/seed_pwr_skills_notion_pages.py)** (`SKILL_ROWS`) | Which rows the hub seed creates; **must** match [`docs/SKILLS_PUBLICATION_CATALOG.md`](docs/SKILLS_PUBLICATION_CATALOG.md) here. |
| **This repo** | **`skills-by-PWR-LABS`** | Catalog + playbook + public packs — push here for the world to see. |

There is **no** doc mirror chain through ribosome for the catalog or playbook: edit **`docs/`** and **`skills/`** here and push **this** repo.

---

## Docs in [skills.]

| Doc | Purpose |
| --- | --- |
| [`AGENTS.md`](AGENTS.md) | Short directive for agents in **this** repo. |
| [`docs/SKILLS_PUBLICATION_CATALOG.md`](docs/SKILLS_PUBLICATION_CATALOG.md) | Machine index — **21** curated skills, Notion tagging, links to **`skills/<skill_id>/`** in this repo. |
| [`docs/SKILLS_NOTION_HUB_PLAYBOOK.md`](docs/SKILLS_NOTION_HUB_PLAYBOOK.md) | Hub layout, row semantics, accents, and how to run the skills-hub sync from nucleus. |
| [`skills/README.md`](skills/README.md) | How to refresh vendored packs from product checkouts. |

Keep the catalog aligned with **`SKILL_ROWS`** + hub sync whenever you add or retire a catalog skill.
