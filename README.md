# [skills.] by [PWR] LABS

Public home for **[skills.]** documentation: the **Notion-ready catalog** and the **skills hub playbook** both live **in this repository** so readers never depend on private product repos for those files.

- **Notion hub:** [skills by PWR LABS](https://www.notion.so/skills-by-PWR-LABS-35d50bc778328020a178d10e7a091bee)
- **GitHub (hyphenated remote name):** [nmaitochondria/skills-by-PWR-LABS](https://github.com/nmaitochondria/skills-by-PWR-LABS) — this folder is your local checkout beside **golgi**, **nucleus**, **ribosome**, etc. (spaces in the directory name are intentional for Cursor layout.)

**Operator automation** (Notion seed, env, vendored `SKILL.md` **packs** for raw URLs) runs from **[PWR-LABS/nucleus](https://github.com/PWR-LABS/nucleus)** — see [`docs/NUCLEUS_PUBLICATION_PLAYBOOK.md`](https://github.com/PWR-LABS/nucleus/blob/main/docs/NUCLEUS_PUBLICATION_PLAYBOOK.md). You do **not** need a separate “skills agent” beyond this public doc tree plus a **[nucleus.]-like executor** (any runner that follows that playbook with its own Notion/env secrets). The public nucleus checkout is the reference implementation today; it is intentionally single-operator and carries the portfolio token burden, not a hosted product every reader must adopt.

---

## Git vs this repo

| Layer | Where it lives | What it is |
| --- | --- | --- |
| **Authoring** | Each product checkout (e.g. `ribosome/.cursor/skills/…`, `chaperone/.cursor/skills/…`, `nucleus/.cursor/skills/…`) | Canonical `SKILL.md` sources for Cursor and git history. |
| **Public packs** | **[PWR-LABS/nucleus `skills/`](https://github.com/PWR-LABS/nucleus/tree/main/skills)** | Full **per–skill-id** trees (`skills/<skill_id>/`) so Notion + READMEs can use **stable raw URLs** without exposing private orgs. Refreshed from sibling checkouts when skills change (see nucleus [`skills/README.md`](https://github.com/PWR-LABS/nucleus/blob/main/skills/README.md)). |
| **Machine list** | **[nucleus `scripts/seed_pwr_skills_notion_pages.py`](https://github.com/PWR-LABS/nucleus/blob/main/scripts/seed_pwr_skills_notion_pages.py)** (`SKILL_ROWS`) | Single source for which rows the hub seed creates; **must** match [`docs/SKILLS_PUBLICATION_CATALOG.md`](docs/SKILLS_PUBLICATION_CATALOG.md) in **this** repo. |
| **This repo** | **`skills-by-PWR-LABS`** (this checkout) | **Only** the human-facing **catalog** + **Notion playbook** — not a second copy of every `SKILL.md`, and **not** “sync docs from ribosome.” |

There is **no** doc mirror chain through ribosome for the catalog or playbook: edit **`docs/`** here and push **this** repo.

---

## Docs in [skills.]

| Doc | Purpose |
| --- | --- |
| [`AGENTS.md`](AGENTS.md) | Short directive for agents in **this** repo: docs vs nucleus execution, authoring repo vs Notion tag. |
| [`docs/SKILLS_PUBLICATION_CATALOG.md`](docs/SKILLS_PUBLICATION_CATALOG.md) | Machine index — **20** curated skills, Notion tagging, links to public `SKILL.md` packs on **PWR-LABS/nucleus** `skills/`. |
| [`docs/SKILLS_NOTION_HUB_PLAYBOOK.md`](docs/SKILLS_NOTION_HUB_PLAYBOOK.md) | Hub layout, row semantics, accents, and how to run the skills-hub sync from nucleus. |

Keep these two files aligned with **`SKILL_ROWS`** + hub sync whenever you add or retire a catalog skill.
