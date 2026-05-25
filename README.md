# [skills.] by [PWR] LABS

Public home for **[skills.]**: the **catalog**, **downloadable skill packs** (`skills/<skill_id>/`), and publication playbook — all in **this repository**.

| Surface | Link |
| --- | --- |
| **Live catalog** | [pwr-labs.ai/chromosomes](https://pwr-labs.ai/chromosomes) |
| **GitHub catalog** | [`docs/SKILLS_PUBLICATION_CATALOG.md`](docs/SKILLS_PUBLICATION_CATALOG.md) |
| **Browse packs** | [`skills/`](skills/) |

Local checkout folder name may include spaces (`skills by PWR LABS`) beside **golgi**, **nucleus**, **ribosome**, etc.

---

## Git vs this repo

| Layer | Where it lives | What it is |
| --- | --- | --- |
| **Authoring** | Each product checkout (e.g. `ribosome/.cursor/skills/…`) | Canonical `SKILL.md` sources for Cursor and git history. |
| **Public packs** | **This repo [`skills/`](skills/)** | Full **per–skill-id** trees for browse/clone/raw URLs. |
| **Machine list** | **[nucleus `SKILL_ROWS`](https://github.com/PWR-LABS/nucleus/blob/main/scripts/seed_pwr_skills_notion_pages.py)** | Audit parity with the catalog — must match [`docs/SKILLS_PUBLICATION_CATALOG.md`](docs/SKILLS_PUBLICATION_CATALOG.md). |
| **Public site** | **[pwr-labs.ai](https://pwr-labs.ai/chromosomes)** | Immersive catalog UI; reads catalog markdown from GitHub. |

Edit **`docs/`** and **`skills/`** here and push **this** repo. There is no doc mirror chain through ribosome.

---

## Docs in [skills.]

| Doc | Purpose |
| --- | --- |
| [`AGENTS.md`](AGENTS.md) | Short directive for agents in **this** repo. |
| [`docs/SKILLS_PUBLICATION_CATALOG.md`](docs/SKILLS_PUBLICATION_CATALOG.md) | Machine index — **21** curated skills, product tags, links to **`skills/<skill_id>/`**. |
| [`docs/SKILLS_PUBLICATION_PLAYBOOK.md`](docs/SKILLS_PUBLICATION_PLAYBOOK.md) | How to refresh packs, publish to GitHub + site. |
| [`docs/SKILLS_NOTION_HUB_PLAYBOOK.md`](docs/SKILLS_NOTION_HUB_PLAYBOOK.md) | **Archived** — former Notion hub layout (retired). |
| [`skills/README.md`](skills/README.md) | How to refresh vendored packs from product checkouts. |

Keep the catalog aligned with **`SKILL_ROWS`** whenever you add or retire a catalog skill.
