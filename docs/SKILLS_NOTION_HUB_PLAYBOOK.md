# [PWR] LABS skills hub — Notion layout playbook

Use this when filling **[skills by PWR LABS (Notion)](https://www.notion.so/skills-by-PWR-LABS-35d50bc778328020a178d10e7a091bee)** and the **[skills database](https://www.notion.so/35d50bc7783280fd9fdeea5a5a7efbbe?v=35d50bc77832809b8fad000c2af850d7)** (one row / page per `SKILL.md`). Property columns are already yours to own; map them to the fields below where it helps.

**Canonical machine list:** [`docs/SKILLS_PUBLICATION_CATALOG.md`](SKILLS_PUBLICATION_CATALOG.md) — **in this same public repo** ([skills.] by [PWR] LABS on GitHub).

**Operator scripts** (seed, layered copy): [PWR-LABS/nucleus](https://github.com/PWR-LABS/nucleus) — `scripts/seed_pwr_skills_notion_pages.py`, `scripts/pwr_skills_public_layer.py`, `bash scripts/run_portfolio_notion.sh skills-hub`. **Public `SKILL.md` trees** for downloads: [nucleus `skills/`](https://github.com/PWR-LABS/nucleus/tree/main/skills).

---

## 1. Accent color (match product doctrine + investor pack)

Use the **same portfolio semantics** as **[nucleus `docs/NUCLEUS_DESIGN_LANGUAGE_BASELINE.md`](https://github.com/PWR-LABS/nucleus/blob/main/docs/NUCLEUS_DESIGN_LANGUAGE_BASELINE.md)** (inherits bracket + Notion color guidance): product-colored **text**, not noisy background fills on whole sections.

| Parent surface | YAML signal | Notion **named** text color (manual pages / highlights) | Hex reference (diagrams / custom CSS) |
| --- | --- | --- | --- |
| **[ribosome.]** | `skill_pack: "[ribosome.]"` | **Yellow** | `#dfab10` |
| **[ribosomal.]** | `skill_pack: "[ribosomal.]"` | **Brown** | `#997655` |
| **[golgi.]** | `skill_pack: "[golgi.]"` | **Blue** | `#2383e2` |
| **[synthesis.]** | `skill_pack: "[synthesis.]"` | **Green** | `#2d9c4a` |
| **[chaperone.]** | `skill_pack: "[chaperone.]"` | **Pink** | bracket ink ≈ `#b42858` |
| **Governance** (no product pack) | `skill_category: governance` (no `skill_pack`) | **Purple** — same umbrella role as **`[PWR] LABS`** | `#7956da` |

**How to apply on a skill page:** tint the **title line** or first **callout** border, section headings for code paths, and any “Skill id / repo” labels with that row’s accent. Keep body prose neutral (black/gray) for readability. Do **not** paste secrets, tokens, database ids, or private customer detail—link to **public** GitHub paths only.

---

## 2. Page body — product doctrine shape (sans secrets)

Each skill page in the DB is a **mini doctrine**: same *shape* as a product `PRODUCT_DOCTRINE.md`, shrunk to one skill. The seed script applies **playbook text colors** to bracket tokens (**`[PWR]`**, **`[PWR] LABS`**, **`[skills.]`**, **`[ribosome.]`** … **`[chaperone.]`**) in unlock / origin / broad bullets and in toggle titles — same palette as §1.

Seeded pages from git open with the **three-layer investor frame** inside **Notion toggles** (canonical copy in nucleus **`scripts/pwr_skills_public_layer.py`**): **dividers between** the three investor toggles, **one divider** after **Broader applications** before **Operating spine**, **no** leading page divider.

1. **Executive summary — what this unlocks** — generic value (what function it serves for any org).
2. **Origin in the [PWR] LABS ecosystem** — where it lives among **[ribosome.]**, **[golgi.]**, governance skills, etc.
3. **Broader applications** — bullets for reuse beyond this stack.

Then the doctrine-shaped spine continues (see seed layout for §0–§8 headings).

Skip heavy architecture treatises unless the skill truly needs them; doctrine pages remain the home for full product narrative.

---

## 3. Database row (your “terminal table”)

For each catalog row, align properties so the **gallery / table** reads like a control surface:

| Suggested semantic | Typical content |
| --- | --- |
| **Title** | Stable **skill id** — same string Cursor uses and the **public** `skills/<skill_id>/` folder name |
| **Description** | Outcome-first label from **`SKILL_ROWS`**, then YAML `description:`, then unlock summary from **`pwr_skills_public_layer.py`** |
| **Governance** | On iff `skill_category: governance` |
| **Product** | Single select **`[ribosome.]`** … or empty when Governance |
| **Repo** | `ribosome` / `chaperone` / … |
| **GitHub URL** | Prefer **nucleus** public `skills/<skill_id>/` tree + raw `SKILL.md` (see catalog) |

Link the **portfolio hub page** to this database with a linked view so the hub stays the narrative entry and the DB stays the index.

---

## 4. Hub page (portfolio) content

On **[skills by PWR LABS (Notion)](https://www.notion.so/skills-by-PWR-LABS-35d50bc778328020a178d10e7a091bee)**:

- Short **why** (public skills; private code is OK; links use public GitHub only).
- Linked **database view** of all skill pages.
- Optional callout: bracket colors match **`[PWR] LABS`** product map (see §1).

---

## 5. Seed / refresh database rows (git → Notion)

**Run from [PWR-LABS/nucleus](https://github.com/PWR-LABS/nucleus) root** (portfolio tooling lives there):

```bash
bash scripts/run_portfolio_notion.sh skills-hub
# or, from nucleus with venv + PYTHONPATH=scripts:
# python3 scripts/seed_pwr_skills_notion_pages.py --apply --refresh-bodies
```

- Auth: **`NOTION_PWR_LABS_TOKEN`** only — set explicitly in **nucleus** **`.env`**. Integration must have access to the skills database.
- Default database id: **`NOTION_PWR_SKILLS_DATABASE_ID`** or `35d50bc7783280fd9fdeea5a5a7efbbe`.
- **Catalog + playbook URLs** in Notion bodies point at **this public repo** (`GITHUB_PWR_SKILLS_DOC_ORG` / `GITHUB_PWR_SKILLS_DOC_REPO` in nucleus `.env` when your GitHub slug differs from the default).

**Refresh existing bodies:** `--refresh-bodies` deletes direct child blocks on each matched page and re-appends the latest layout. Large pages can take **several minutes**.

---

## 6. See also

- **[This repo `README.md`](../README.md)** — **Docs in [skills.]** entry point.
- **[nucleus `docs/NUCLEUS_PUBLICATION_PLAYBOOK.md`](https://github.com/PWR-LABS/nucleus/blob/main/docs/NUCLEUS_PUBLICATION_PLAYBOOK.md)** — investor + skills hub commands.
- **[nucleus `docs/NOTION_DOCTRINE_SYNC_OWNERSHIP.md`](https://github.com/PWR-LABS/nucleus/blob/main/docs/NOTION_DOCTRINE_SYNC_OWNERSHIP.md)** — which Notion token owns which surface.
