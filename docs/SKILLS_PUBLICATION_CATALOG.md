# Skills publication catalog (Notion-ready)

**Authoritative public index for [skills.]** — this file lives in **this repository** ([skills-by-PWR-LABS](https://github.com/nmaitochondria/skills-by-PWR-LABS) on GitHub). Link it from Notion, the hub README, and anywhere you need a stable URL that does **not** depend on private product repos.

**Machine list:** `SKILL_ROWS` in [PWR-LABS/nucleus `scripts/seed_pwr_skills_notion_pages.py`](https://github.com/PWR-LABS/nucleus/blob/main/scripts/seed_pwr_skills_notion_pages.py) must stay in lockstep with the tables below (skill id, **authoring repo**, `.cursor/skills/` folder). Hub sync runs from **nucleus**; the public **catalog** and **`skills/<skill_id>/` packs** live in **this repo**.

**Public `SKILL.md` downloads:** vendored trees live under [`skills/`](https://github.com/nmaitochondria/skills-by-PWR-LABS/tree/main/skills) in **this repository** as `skills/<skill_id>/` (full copy for each catalog id). Raw file pattern:

`https://raw.githubusercontent.com/nmaitochondria/skills-by-PWR-LABS/main/skills/<skill_id>/SKILL.md`

**Notion layout + hub cadence:** [`SKILLS_NOTION_HUB_PLAYBOOK.md`](SKILLS_NOTION_HUB_PLAYBOOK.md) in this same repo.

**Public Notion hub:** [skills by PWR LABS](https://www.notion.so/skills-by-PWR-LABS-35d50bc778328020a178d10e7a091bee) — linked database + portfolio entry.

**Table columns:** **Authoring repo** is the checkout where you edit `SKILL.md` (clone + path). It **can differ** from the Notion **`[product.]`** heading above a block—Notion tags are domain/read-surface; authoring location is where the file actually lives in git.

---

## Notion tagging rules

| YAML | Notion behavior |
| --- | --- |
| **`skill_category: governance`** | **Governance** / `[PWR] LABS governance` only — no product pack tag. |
| **`skill_category: product_pack`** + **`skill_pack: "[product.]"`** | Exactly one product select: **`[ribosome.]`, `[golgi.]`, `[chaperone.]`, `[ribosomal.]`, `[synthesis.]`, …** |

---

## I. Governance (`skill_category: governance`, no `skill_pack`)

| skill_id (Notion title) | Authoring repo | Canonical path | Public pack (this repo `skills/`) |
| --- | --- | --- | --- |
| `align-cross-repo-doctrine-connector-handoff` | ribosome | `.cursor/skills/align-cross-repo-doctrine-connector-handoff/SKILL.md` | [`skills/align-cross-repo-doctrine-connector-handoff/`](https://github.com/nmaitochondria/skills-by-PWR-LABS/tree/main/skills/align-cross-repo-doctrine-connector-handoff) |
| `portfolio-wide-governance` | nucleus | `.cursor/skills/nucleus-global-admin/SKILL.md` | [`skills/portfolio-wide-governance/`](https://github.com/nmaitochondria/skills-by-PWR-LABS/tree/main/skills/portfolio-wide-governance) |
| `append-only-connector-directive-log` | ribosome | `.cursor/skills/append-only-connector-directive-log/SKILL.md` | [`skills/append-only-connector-directive-log/`](https://github.com/nmaitochondria/skills-by-PWR-LABS/tree/main/skills/append-only-connector-directive-log) |
| `sync-markdown-notion-dossiers` | ribosome | `.cursor/skills/sync-markdown-notion-dossiers/SKILL.md` | [`skills/sync-markdown-notion-dossiers/`](https://github.com/nmaitochondria/skills-by-PWR-LABS/tree/main/skills/sync-markdown-notion-dossiers) |
| `isolate-notion-integrations-by-risk` | ribosome | `.cursor/skills/isolate-notion-integrations-by-risk/SKILL.md` | [`skills/isolate-notion-integrations-by-risk/`](https://github.com/nmaitochondria/skills-by-PWR-LABS/tree/main/skills/isolate-notion-integrations-by-risk) |
| `cross-repo-edge-audit` | nucleus | `.cursor/skills/cross-repo-edge-audit/SKILL.md` | [`skills/cross-repo-edge-audit/`](https://github.com/nmaitochondria/skills-by-PWR-LABS/tree/main/skills/cross-repo-edge-audit) |

---

## II. Product packs (`skill_category: product_pack`, one `[product.]` each)

### `[ribosome.]`

| skill_id | Authoring repo | Canonical path | Public pack |
| --- | --- | --- | --- |
| `job-search-tracker-rituals` | ribosome | `.cursor/skills/job-search-tracker-rituals/SKILL.md` | [`skills/job-search-tracker-rituals/`](https://github.com/nmaitochondria/skills-by-PWR-LABS/tree/main/skills/job-search-tracker-rituals) |
| `clinician-nonclinical-job-narrative` | ribosome | `.cursor/skills/clinician-nonclinical-job-narrative/SKILL.md` | [`skills/clinician-nonclinical-job-narrative/`](https://github.com/nmaitochondria/skills-by-PWR-LABS/tree/main/skills/clinician-nonclinical-job-narrative) |

### `[chaperone.]`

| skill_id | Authoring repo | Canonical path | Public pack |
| --- | --- | --- | --- |
| `structured-gdoc-notion-application-ingest` | chaperone | `.cursor/skills/structured-gdoc-notion-application-ingest/SKILL.md` | [`skills/structured-gdoc-notion-application-ingest/`](https://github.com/nmaitochondria/skills-by-PWR-LABS/tree/main/skills/structured-gdoc-notion-application-ingest) |
| `notion-activity-counter-parity-refresh` | chaperone | `.cursor/skills/notion-activity-counter-parity-refresh/SKILL.md` | [`skills/notion-activity-counter-parity-refresh/`](https://github.com/nmaitochondria/skills-by-PWR-LABS/tree/main/skills/notion-activity-counter-parity-refresh) |
| `admissions-doctrine-notion-sync` | chaperone | `.cursor/skills/admissions-doctrine-notion-sync/SKILL.md` | [`skills/admissions-doctrine-notion-sync/`](https://github.com/nmaitochondria/skills-by-PWR-LABS/tree/main/skills/admissions-doctrine-notion-sync) |
| `bounded-integrity-admissions-coaching` | chaperone | `.cursor/skills/bounded-integrity-admissions-coaching/SKILL.md` | [`skills/bounded-integrity-admissions-coaching/`](https://github.com/nmaitochondria/skills-by-PWR-LABS/tree/main/skills/bounded-integrity-admissions-coaching) |
| `secondary-application-blitz-cadence` | chaperone | `.cursor/skills/secondary-application-blitz-cadence/SKILL.md` | [`skills/secondary-application-blitz-cadence/`](https://github.com/nmaitochondria/skills-by-PWR-LABS/tree/main/skills/secondary-application-blitz-cadence) |

### `[golgi.]`

| skill_id | Authoring repo | Canonical path | Public pack |
| --- | --- | --- | --- |
| `trusted-media-acquisition-chain` | golgi | `.cursor/skills/trusted-media-acquisition-chain/SKILL.md` | [`skills/trusted-media-acquisition-chain/`](https://github.com/nmaitochondria/skills-by-PWR-LABS/tree/main/skills/trusted-media-acquisition-chain) |
| `dj-session-environment-preflight` | golgi | `.cursor/skills/dj-session-environment-preflight/SKILL.md` | [`skills/dj-session-environment-preflight/`](https://github.com/nmaitochondria/skills-by-PWR-LABS/tree/main/skills/dj-session-environment-preflight) |
| `metadata-tagger-prep-bridge` | golgi | `.cursor/skills/metadata-tagger-prep-bridge/SKILL.md` | [`skills/metadata-tagger-prep-bridge/`](https://github.com/nmaitochondria/skills-by-PWR-LABS/tree/main/skills/metadata-tagger-prep-bridge) |

### `[ribosomal.]`

| skill_id | Authoring repo | Canonical path | Public pack |
| --- | --- | --- | --- |
| `outbound-vs-central-executor-scope` | ribosomal | `.cursor/skills/outbound-vs-central-executor-scope/SKILL.md` | [`skills/outbound-vs-central-executor-scope/`](https://github.com/nmaitochondria/skills-by-PWR-LABS/tree/main/skills/outbound-vs-central-executor-scope) |
| `apollo-notion-outbound-preflight` | ribosomal | `.cursor/skills/apollo-notion-outbound-preflight/SKILL.md` | [`skills/apollo-notion-outbound-preflight/`](https://github.com/nmaitochondria/skills-by-PWR-LABS/tree/main/skills/apollo-notion-outbound-preflight) |
| `outbound-notion-approval-navigation` | ribosomal | `.cursor/skills/outbound-notion-approval-navigation/SKILL.md` | [`skills/outbound-notion-approval-navigation/`](https://github.com/nmaitochondria/skills-by-PWR-LABS/tree/main/skills/outbound-notion-approval-navigation) |

### `[synthesis.]`

| skill_id | Authoring repo | Canonical path | Public pack |
| --- | --- | --- | --- |
| `connector-dialogue-doctrine-fold` | synthesis | `.cursor/skills/connector-dialogue-doctrine-fold/SKILL.md` | [`skills/connector-dialogue-doctrine-fold/`](https://github.com/nmaitochondria/skills-by-PWR-LABS/tree/main/skills/connector-dialogue-doctrine-fold) |
| `doctrine-vs-retrieval-arbitration` | synthesis | `.cursor/skills/doctrine-vs-retrieval-arbitration/SKILL.md` | [`skills/doctrine-vs-retrieval-arbitration/`](https://github.com/nmaitochondria/skills-by-PWR-LABS/tree/main/skills/doctrine-vs-retrieval-arbitration) |

---

## III. Not in this catalog (by design)

- **`synthesis/.cursor/skills/tooluniverse-*`** — vendor/framework scale; optional separate Notion row if you add one.

---

## Row count

**21** curated PWR `SKILL.md` entries. If the Notion database shows an extra row, treat it as duplicate / scratch / legacy until reconciled with this index.

After you change a canonical `SKILL.md`, refresh the vendored tree under **this repo** `skills/<skill_id>/` (see [`skills/README.md`](../skills/README.md)), push **skills-by-PWR-LABS**, then run the hub sync from **nucleus** — [`SKILLS_NOTION_HUB_PLAYBOOK.md`](SKILLS_NOTION_HUB_PLAYBOOK.md) §5.
