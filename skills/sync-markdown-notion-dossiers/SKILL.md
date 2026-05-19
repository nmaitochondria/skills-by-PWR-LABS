---
name: sync-markdown-notion-dossiers
description: >-
  Syncs Product Preview / investor Markdown and [ribosome.] product doctrine from git to Notion:
  NOTION_TOKEN + --notion-sync-investor-doctrine; NOTION_RIBOSOME_DOCTRINE_PAGE_ID + notion_ribosome_token()
  (typically NOTION_RIBOSOME_TOKEN) + --notion-sync-product-doctrine. Use when explaining **[PWR]** vs hub tokens.
skill_category: governance
# Notion: **Governance** — [PWR] LABS token + Product Preview / doctrine sync (applies wherever those pages are edited).
disable-model-invocation: false
---

# Sync [PWR] Notion dossiers

## What this unlocks

Publishes **investor- and operator-facing doctrine distillates** from Markdown to Notion using the **[PWR] LABS** integration surface—so Product Preview and related dossiers stay aligned with git.

## Origin in the [PWR] ecosystem

Wires **`NOTION_TOKEN`** in **ribosome** for `--notion-sync-investor-doctrine` (Product Preview / investor Markdown), and **`notion_ribosome_token()`** (usually **`NOTION_RIBOSOME_TOKEN`**) for **`--notion-sync-product-doctrine`**—so **[PWR]** dossiers stay isolated from the hub job-search surface unless you intentionally share a page with both integrations.

## Broader applications

- Any founder maintaining a live Notion “dossier” beside a private Git repo.
- Versioned narrative pages that must track a dated title or changelog stamp.
- Portfolio or fund materials where Markdown remains canonical but Notion is the reading room.

## What this is

**[PWR] LABS** covers **Product Preview** (investor-facing distillate from `docs/INVESTOR_PACK_NOTION_SOURCE.md`) via **`NOTION_TOKEN`** and **`--notion-sync-investor-doctrine`**.

**[ribosome.]** product doctrine (`NOTION_RIBOSOME_DOCTRINE_PAGE_ID`, **`--notion-sync-product-doctrine`**) uses the **hub** secret from **`notion_ribosome_token()`** (precedence in **`notion_env.py`**). Job-search databases and tracker flows use the same hub chain — see **isolate-notion-integrations-by-risk** for why tokens must not be swapped.

## Environment (ribosome repo)

| Variable | Role |
|----------|------|
| `NOTION_TOKEN` | **[PWR] LABS** secret — required for `--notion-sync-investor-doctrine`. |
| `NOTION_RIBOSOME_TOKEN` (or unset → falls back to `NOTION_TOKEN`) | **[ribosome.]** hub — used by `--notion-sync-product-doctrine` via `notion_ribosome_token()`. |
| `NOTION_INVESTOR_DOCTRINE_PAGE_ID` | Product Preview page id (32 hex). |
| `INVESTOR_DOCTRINE_VERSION` | Version string embedded in title (e.g. `05.07.26`). |
| `NOTION_INVESTOR_DOCTRINE_TITLE_TEMPLATE` | Optional; default **`[PWR] LABS – Product Preview v{version}`**. |
| `INVESTOR_PACK_NOTION_SOURCE_PATH` | Default `docs/INVESTOR_PACK_NOTION_SOURCE.md`. |
| `NOTION_RIBOSOME_DOCTRINE_PAGE_ID` | Product doctrine Notion page id (32 hex) for `--notion-sync-product-doctrine`. |
| `RIBOSOME_DOCTRINE_VERSION` | Version string for title / Last synced (e.g. `05.07.26`). |

## CLI

```bash
python3 ribosome.py --notion-sync-investor-doctrine --verbose
python3 ribosome.py --notion-sync-product-doctrine --verbose
```

**Investor / Product Preview** uses **`NOTION_TOKEN`** only. **Product doctrine** uses **`notion_ribosome_token()`** (hub first, then legacy **`NOTION_TOKEN`** fallback).

## Boundaries

- Do **not** aim **`--notion-sync-investor-doctrine`** at **[ribosome.]** job databases — that command is **[PWR] LABS** only.
- **`--notion-sync-product-doctrine`** must target a page shared with whichever integration **`notion_ribosome_token()`** resolves to (often **`NOTION_RIBOSOME_TOKEN`** when split).

