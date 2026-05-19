---
name: dj-session-environment-preflight
description: >-
  Preflights golgi DJ session environment: doctor --json, path and slskd/ffmpeg checks, acquire mini-status,
  advisory Soulseek configuration. Use before a long acquire session or after moving machines.
skill_category: product_pack
skill_pack: "[golgi.]"
disable-model-invocation: true
---

# Preflight DJ session environment

## What this unlocks

Runs a **pre-flight gate** before trusting a long session: paths, ffmpeg/slskd sanity, and advisory health JSON so class-of-errors fails early instead of mid-crate.

## Origin in the [PWR] ecosystem

**[golgi.]** session discipline: complements **`trusted-media-acquisition-chain`** as aviation-style checks before acquisition.

## Broader applications

- Any local-first creative toolchain with fragile path/config coupling.
- Data science environments before long GPU or cluster jobs.
- Field operations checklists mapped to CLI `doctor` equivalents.

## When to use

- **Before** leaning on **`queue try-acquire`** for a long crate session.
- After **config drift** (`paths.local.yaml`, slskd, Spotify tokens) or a **fresh clone**.

## Commands (orientation)

```bash
# Advisory health check (paths, ffmpeg/ffprobe, slskd hints)
golgi doctor --json

# Pending / swept visibility for mini downloads folder (when configured)
golgi acquire mini-status
```

Exact CLI surface names follow **`docs/PRODUCT_DOCTRINE.md`** codebook — this skill is the **operator story**: preflight does **not** replace QC or routing; it catches **class-of-errors** early (missing folders, broken ffmpeg, sad slskd config).

## What “good” looks like

- **`doctor --json`** returns actionable JSON without silent “looks fine” when paths are wrong.
- Operator knows **`folders.soulseek_downloads`**, **`folders.to_tag`**, optional staging folders exist and match **`config/paths*.yaml`**.

## Limits

- Spectral QC heuristics are **heuristic**, not forensic proof of authenticity.
- **Local secrets** (`.env`, **`config/paths.local.yaml`**) are **not in git** — each machine must copy from examples.

## Cross-skill

- **`trusted-media-acquisition-chain`** — execute acquisition after preflight is clean.

