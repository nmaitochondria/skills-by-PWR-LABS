---
name: trusted-media-acquisition-chain
description: >-
  Trust chain for golgi DJ acquisition: acquire_attempt_id, provenance sidecars,
  queue try-acquire routing to to_tag/to_convert, QC gates, mark-imported vs acquire pipeline.
  Use when debugging Soulseek downloads, post-QC moves, or why rows look populated but crates are wrong.
skill_category: product_pack
skill_pack: "[golgi.]"
disable-model-invocation: true
---

# Trust DJ acquisition chain

## What this unlocks

Makes **local acquisition trustworthy**: attempt IDs, provenance sidecars, queue routing, and explicit separation between “marked imported” and “pipeline moved”—so crates do not lie about history.

## Origin in the [PWR] ecosystem

**[golgi.]** Soulseek / acquisition lane: encodes the trust spine that ends at QC/routing before tagging and metadata prep.

## Broader applications

- Any file-ingest pipeline where provenance and attempt correlation matter (media, lab instruments, ETL).
- Operator-run systems where “looks populated” must not mask wrong routing.
- Teaching junior operators how queue semantics differ from filesystem moves.

## When to use

- Explaining **why a file is trusted** from candidate pick through **`to_tag`** / **`to_convert`**.
- Choosing between **`queue mark-imported`** and **`acquire pipeline`** after QC.

## Spine (non-negotiables)

1. **`acquire_attempt_id`** (UUID) per try-acquire attempt; correlate optional slskd transfer ids when resolvable.
2. **`{stem}.golgi_provenance.json`** sidecars — auditable path from listing → local bytes.
3. **Post-QC routing** — **`queue try-acquire`** moves winners per pool rules; ignored extensions (e.g. **`.m4a`**) are **not** enqueued.
4. **`queue mark-imported`** — sets **`acquired_qc_pass`** **without** moving files under **`soulseek_downloads`**; use **`acquire pipeline`** when files still need pipeline movement.

## Pool routing (mental model)

Soulseek pool routes **`.mp3`** and native **AIFF** toward **`to_tag`**; **`.flac` / `.wav` / `.wavpack`** through optional **`folders.to_convert`** then AIFF to **`to_tag`**. **`acquire mini-status`** surfaces pending/swept counts for **`folders.mini_music_downloads`**.

## Verification

- Inspect **queue JSON** + terminal JSON from **`queue try-acquire`** (including optional **`purchase_links`**).
- If spectrogram auto-review is enabled, treat policy as **`soulseek.try_acquire`** — not a substitute for listening judgment.

## Docs

- **`docs/PRODUCT_DOCTRINE.md`** — snapshot + queue narrative + §8 changelog.
- **`docs/CONNECTOR_DIALOGUE_THREAD.md`** — durable coordination.

## Cross-skill

- **`dj-session-environment-preflight`** — run **`doctor --json`** before trusting a session.
- **`align-cross-repo-doctrine-connector-handoff`** — where this repo sits in PWR documentation loop.

