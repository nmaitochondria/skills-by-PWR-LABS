# [skills.] — publication playbook (GitHub + site)

**Public surfaces (canonical):**

| Surface | URL |
| --- | --- |
| **Live catalog (site)** | [pwr-labs.ai/chromosomes](https://pwr-labs.ai/chromosomes) — parsed from this repo’s catalog markdown |
| **Catalog (git)** | [`docs/SKILLS_PUBLICATION_CATALOG.md`](SKILLS_PUBLICATION_CATALOG.md) |
| **Skill packs** | [`skills/<skill_id>/`](https://github.com/nmaitochondria/skills-by-PWR-LABS/tree/main/skills) |

The former **Notion skills hub** is **retired** (2026-05). Do not link readers to it. Archive reference only: [`SKILLS_NOTION_HUB_PLAYBOOK.md`](SKILLS_NOTION_HUB_PLAYBOOK.md).

---

## 1. Accent colors (portfolio map)

Same bracket semantics as **[nucleus design baseline](https://github.com/PWR-LABS/nucleus/blob/main/docs/NUCLEUS_DESIGN_LANGUAGE_BASELINE.md)** and **pwr-labs.ai** chromosomes UI:

| Product | YAML `skill_pack` | Hex |
| --- | --- | --- |
| **[ribosome.]** | `"[ribosome.]"` | `#dfab10` |
| **[ribosomal.]** | `"[ribosomal.]"` | `#997655` |
| **[golgi.]** | `"[golgi.]"` | `#2383e2` |
| **[synthesis.]** | `"[synthesis.]"` | `#2d9c4a` |
| **[chaperone.]** | `"[chaperone.]"` | `#b42858` |
| **Governance** | `skill_category: governance` (no pack) | `#7956da` |

---

## 2. When you change a skill

1. Edit **`SKILL.md`** in the product checkout (e.g. `ribosome/.cursor/skills/…`).
2. Refresh the public pack in **this repo**:
   ```bash
   rsync -a ../ribosome/.cursor/skills/<skill-id>/ "./skills/<skill-id>/"
   ```
3. Update **[`docs/SKILLS_PUBLICATION_CATALOG.md`](SKILLS_PUBLICATION_CATALOG.md)** if id, repo, or path changed.
4. Keep **`SKILL_ROWS`** in [nucleus `scripts/seed_pwr_skills_notion_pages.py`](https://github.com/PWR-LABS/nucleus/blob/main/scripts/seed_pwr_skills_notion_pages.py) aligned with the catalog (machine list for audits — **not** for Notion sync).
5. Push **skills-by-PWR-LABS**; site catalog updates on next deploy when it pulls raw markdown from GitHub.

---

## 3. Operator checks (nucleus)

| Check | Command |
| --- | --- |
| Catalog parity | From **ribosome**: `pytest tests/test_pwr_skills_catalog_parity.py -q` |
| Cross-repo edges | From **nucleus**: `python3 scripts/audit_cross_repo_edges.py` |

**Do not run** `bash scripts/run_portfolio_notion.sh skills-hub` unless explicitly reviving the archived Notion hub.

---

## 4. See also

- [`README.md`](../README.md) — repo entry
- [`skills/README.md`](../skills/README.md) — pack refresh
- [nucleus publication playbook](https://github.com/PWR-LABS/nucleus/blob/main/docs/NUCLEUS_PUBLICATION_PLAYBOOK.md) — investor + portfolio Notion (separate from public skills)
