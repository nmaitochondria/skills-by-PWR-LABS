---
name: append-only-connector-directive-log
description: >-
  Runs a git-backed connector ↔ agent append-only log: two-layer directives (plain language +
  technical codebook), heading status hygiene, folding durable truth into doctrine and handoff.
  Use when creating, migrating, or cleaning up CONNECTOR_DIALOGUE_THREAD-style files in any repo.
skill_category: governance
# Notion: **Governance** only — portable connector pattern for any repo.
disable-model-invocation: true
---

# Run connector append-only log

## What this unlocks

Establishes a **durable, append-only coordination channel** between humans, connectors, and coding agents—with a two-layer directive style (plain language + technical codebook) so intent survives handoffs.

## Origin in the [PWR] ecosystem

Born from **[PWR] LABS** connector practice (see **`docs/CONNECTOR_DIALOGUE_THREAD.md`** in each repo): the same mechanics apply whether the product is career transition, admissions coaching, or research tooling.

## Broader applications

- Any org running “ChatGPT as connector” alongside Cursor/Codex and needing a git-backed audit trail.
- Incident or design threads that must stay chronological without silent rewrites.
- Regulated or integrity-sensitive workflows where directives need explicit verification blocks.
- Customer-facing programs where you want a portable pattern, not a vendor-specific chat export.

## When to use

- Spinning up **durable agent ↔ connector coordination** beyond one-off chat transcripts.
- User mentions **connector**, **directive**, **running dialogue**, **plain language + codebook**, or **fold into doctrine**.

## File shape (repo convention)

Adapt paths to the project; ribosome uses **`docs/CONNECTOR_DIALOGUE_THREAD.md`**.

1. **Static preamble** — purpose, how to use, timestamp rules, connector writing standard, **Notes**, optional copy-paste prompt for the connector.
2. **`## Running dialogue`** — **single chronological log**; newest entry is always **last**.
3. **Notes** and connector prompt stay **above** **Running dialogue** so the tail stays append-only.

## Each running entry (minimum)

- **Heading** one line: `### YYYY-MM-DDTHH:mm:ss±HH:mm | chatgpt | status: OPEN` (or `agent`, `DONE`, `BLOCKED`, `IN_PROGRESS`).
- **Body**: context, requested or implemented action, links to PRs/commits when useful.
- **Status hygiene:** when in-repo work for a `chatgpt` directive is finished, change that heading to **`DONE`** or **`BLOCKED`** so the log does not look like unanswered work.

## Connector writing standard (two layers)

1. **Plain language** — scenario, trust failure or blocker, what “good” looks like (PM-readable).
2. **Technical codebook** — separated, with concrete anchors: surfaces (CLI flags, env keys, schema names), behavioral spec, **definition of done** (numbered checklist), **verification** commands, positive/negative controls, non-goals, risks/limits.

Prefer **one primary ask per entry**; unrelated work → new entry. Re-read prior **Running dialogue** so the new entry **diffs against current repo truth**.

## Fold-up loop (after implementation)

Stable behavior belongs in durable docs, not only chat:

- **Product / operator truth** — e.g. `PRODUCT_DOCTRINE`, top snapshot, dated changelog.
- **Engineering handoff** — fragile modules, env caveats, commands (`AGENT_HANDOFF` or equivalent).
- **Acceptance / smoke** — copy-paste scenarios when the bar moves (`CANONICAL_QUERIES` or equivalent).

Agent **DONE** replies should name which of the above were updated.

## Timestamps

Use one agreed IANA timezone for the whole file (ribosome: **`America/New_York`** for append-time headings unless the operator specifies otherwise). Stamps are **append time** for the agent writing the line, not guessed history, unless the human explicitly asks to backdate.

## Notion companion (optional)

Publish a short Notion page that links to this repo’s **raw `SKILL.md` on GitHub** and to the live **`CONNECTOR_DIALOGUE_THREAD.md`** path; use **`docs/templates/NOTION_SKILL_COMPANION.md`** in this repo as a starting layout.

## Reference implementation

- [docs/CONNECTOR_DIALOGUE_THREAD.md](../../../docs/CONNECTOR_DIALOGUE_THREAD.md) — full ribosome example with connector prompt and long-running log.

