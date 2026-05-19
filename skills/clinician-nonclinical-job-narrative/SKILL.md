---
name: clinician-nonclinical-job-narrative
description: >-
  Runs clinician-to-industry job-search narrative: credentialing story, pivot vocabulary,
  ribosome Notion env conventions — after job-search-tracker-rituals when user is MD/DO
  moving to non-clinical roles.
skill_category: product_pack
skill_pack: "[ribosome.]"
disable-model-invocation: false
---

# Run job-search med-pivot narrative

## What this unlocks

Adds a **clinician-specific narrative layer** on top of generic job-search discipline: credibility, scope boundaries, and vocabulary for non-clinical roles—without inventing credentials.

## Origin in the [PWR] ecosystem

Overlays **[ribosome.]** workflows when the operator is an **MD/DO** moving to industry paths, after generic tracker rituals are in place.

## Broader applications

- Physician executive or medical affairs transitions needing tone control in outreach and CV lines.
- Any regulated professional pivot where “clinical voice” must be translated, not erased.
- Resume and fit-note generation where the model must not overclaim clinical practice.

## When to use

User is a physician or clinician transitioning to non-clinical roles; needs framing that **job-search-tracker-rituals** does not assume (clinical credibility without clinical practice, scope-of-practice boundaries in narrative).

## Depends on

Apply **[job-search-tracker-rituals](../job-search-tracker-rituals/SKILL.md)** first unless user explicitly declines generic tracker hygiene.

## Additions

- **Narrative:** Translate clinical outcomes into operator-friendly bullets (quality, leadership, systems).
- **CLI ingest:** `ribosome.py --ingest-job-url` passes resume excerpt + job text to OpenAI so **`fit_summary`** reflects physician→industry pivot framing (see `job_ingest.py`).
- **Ribosome:** Reference **career_networking** mode and properties documented in repo `.env.example`; Atherton/sales lane lives in **[ribosomal](https://github.com/nmaitochondria/ribosomal)** — do not mix Apollo keys here.

## Boundaries

- No Apollo sequence orchestration in this skill — use **ribosomal** repo for that lane.
- No shared third-party API keys; user supplies OpenAI/Tavily in their own `.env`.

