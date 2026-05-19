---
name: metadata-tagger-prep-bridge
description: >-
  Bridges golgi metadata policy to Mp3tag prep for `to_tag`: METADATA_POLICY, acquire metadata-ingest,
  prepare-metadata-artwork, metadata-tag-plan vs metadata-tag-write dry-run/apply.
  Use when operators ask about sidecars, Mp3tag practice, or reversible prep before final tags.
skill_category: product_pack
skill_pack: "[golgi.]"
disable-model-invocation: true
---

# Bridge metadata to Mp3tag prep

## What this unlocks

Bridges **policy-defined metadata** into reversible prep for final human tagging—defaulting to dry-run until the operator explicitly applies embedded writes.

## Origin in the [PWR] ecosystem

**[golgi.]** `to_tag` stage: connects **`METADATA_POLICY.md`** with ingest/plan/write CLI mental model after acquisition trust spine completes.

## Broader applications

- Digital asset pipelines where embedded metadata writes are destructive if rushed.
- Archival projects needing conservative mutagen-style tooling patterns beyond audio.
- Quality programs that pair policy docs with CLI guardrails.

## When to use

- Stage **(3)** in the pipeline: after QC and routing into **`3. to tag`**, before final human tagging / export.
- Choosing between **`metadata-tag-plan`** (inspect diffs) and **`metadata-tag-write --apply`** (mutate embedded tags).

## Policy source

- **`docs/METADATA_POLICY.md`** — canonical schema, required vs optional fields, conservative “no silent irreversible writes” posture.
- **`docs/PRODUCT_DOCTRINE.md`** — where **`acquire metadata-ingest`** and **`acquire prepare-metadata-artwork`** sit in the story.

## CLI mental model

1. **`acquire metadata-ingest`** / **`acquire prepare-metadata-artwork`** — capture **safe sidecars** (`*.golgi_metadata_ingest.json`) and artwork prep without pretending tagging is solved.
2. **`metadata-tag-plan`** — review proposed embedded-tag deltas.
3. **`metadata-tag-write`** — default **dry-run**; **`--apply`** only after review.

Embedded writes use **mutagen** across MP3 / FLAC / AIFF per policy.

## Invariants

- Prep is **reversible** where policy allows; default CLI modes favor **dry-run** until operator explicitly applies.
- **`METADATA_POLICY`** and doctrine should move **together** when metadata contracts change (see **`docs/PRODUCT_DOCTRINE.md` §0.1** rule).

## Cross-skill

- **`trusted-media-acquisition-chain`** — trust spine ends at QC/routing; this skill picks up at **`to_tag`** prep.

