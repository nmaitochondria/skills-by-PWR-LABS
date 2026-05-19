---
name: outbound-vs-central-executor-scope
description: >-
  Scopes Atherton / infusion outbound vs ribosome: ribosomal owns workflow contracts and acceptance;
  ribosome is executor plumbing only. Use when agents confuse ribosomal with ribosome career
  networking, or when adopting new Apollo/Notion columns for this lane.
skill_category: product_pack
skill_pack: "[ribosomal.]"
disable-model-invocation: true
---

# Scope outbound vs ribosome executor

## What this unlocks

Draws a **hard lane boundary**: which contracts and semantics belong to the outbound product repo vs which mechanics intentionally reuse a shared executor—preventing silent forks of behavior.

## Origin in the [PWR] ecosystem

**[ribosomal.]** Atherton / outbound lane: canonical contracts and approval semantics live in ribosomal; **`./scripts/ribosomal`** invokes shared executor plumbing only where doctrine explicitly adopts it.

## Broader applications

- Any “thin client product + thick shared runtime” org chart.
- Partner-facing CRM lanes that must not accidentally inherit unrelated CLI modules.
- Security posture where lane env files must stay isolated from personal tooling.

## When to use

- “Where is the **canonical** answer for Atherton?” → **ribosomal first**.
- Deciding whether a new knob belongs in **ribosomal doctrine** or only in upstream **ribosome**.

## One-sentence truth

> **[ribosomal.]** documents and gates the **lane**; **`./scripts/ribosomal`** runs **shared** Apollo ↔ Notion mechanics this doctrine **explicitly adopts**.

## Greenfield scope (§0.2 mental model)

- **Specify in ribosomal first:** tables, columns, env names, operator semantics, priority/scoring rules.
- **Reuse the lane CLI deliberately** only as substrate: sequence upsert, **`--discover`**, unified **`Draft Message`** / **`Outreach message type`**, optional Layout B **Call Prep**, secrets via **`./scripts/ribosomal`** + **`ribosomal/.env`**.
- **Ignore vestiges** of unrelated ribosome features unless **this doctrine** adopts them.

## Operator-facing rule

If an operator asks **how to run**, **what is canonical**, **what changed**, or **which env/status mapping** — answer from **ribosomal** `README`, **`docs/PRODUCT_DOCTRINE.md`**, **`handoff/CANONICAL_QUERIES.md`**, and **`.env.example`** subset **before** pointing at generic ribosome docs.

## This repo has no Python runner

Executable automation lives in **`ribosome`**; ribosomal ships **scripts** that invoke it from the correct cwd with **this repo’s `.env`**.

## Cross-skill

- **`apollo-notion-outbound-preflight`** — concrete script cadence.
- **`align-cross-repo-doctrine-connector-handoff`** — connector/doctrine trio map across PWR repos.

