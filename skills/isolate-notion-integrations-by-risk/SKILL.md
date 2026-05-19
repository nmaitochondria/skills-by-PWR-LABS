---
name: isolate-notion-integrations-by-risk
description: >-
  Separates Notion integrations: NOTION_RIBOSOME_TOKEN ([ribosome.] hub) for Application Tracker,
  profile, Guru Ask, jobs web UI vs NOTION_TOKEN ([PWR] LABS) for Product Preview and doctrine syncs.
  Use when wiring env, debugging wrong-token writes, or explaining hub vs dossier credentials.
skill_category: governance
# Notion: **Governance** — separates hub `NOTION_RIBOSOME_TOKEN` from **[PWR]** `NOTION_TOKEN` (cross-cutting integration hygiene).
disable-model-invocation: false
---

# Split Notion tokens ([PWR] vs [ribosome.] hub)

## What this unlocks

Separates **multiple Notion integrations by risk and audience** so automation never writes customer job data with the same secret that updates investor pages—or vice versa.

## Origin in the [PWR] ecosystem

In **[PWR] LABS**, **`NOTION_TOKEN`** carries **[PWR] LABS** / Product Preview and doctrine surfaces, while **`NOTION_RIBOSOME_TOKEN`** isolates the **[ribosome.]** job-search hub, profile, and jobs web UI.

## Broader applications

- Multi-tenant or multi-brand Notion workspaces with distinct automation scopes.
- Security reviews that need a crisp story: which integration owns which data class.
- Teaching collaborators why “one Notion token everywhere” is a liability at scale.

## Principle

**`NOTION_RIBOSOME_TOKEN`** = **[ribosome.]** — tracker, profile, Guru Ask DB, job dashboard under the hub, **`jobs_web_api`**.

**`NOTION_TOKEN`** = **[PWR] LABS** — Product Preview, **`--notion-sync-investor-doctrine`**, **`--notion-sync-product-doctrine`** when those pages are connected to **[PWR]**.

Do not interchange these secrets.

## Publication

Ship beside **`sync-markdown-notion-dossiers`** so automation and humans keep integrations distinct.

