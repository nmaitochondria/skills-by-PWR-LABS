---
name: secondary-application-blitz-cadence
description: >-
  Operates high-volume secondaries cadence: batching, prompt fidelity, integrity checks,
  and avoiding narrative drift under deadline stress. Use for MD/DO and selective grad lanes
  where many school-specific prompts arrive in a short window.
skill_category: product_pack
skill_pack: "[chaperone.]"
disable-model-invocation: true
---

# Operate secondaries blitz cadence

## What this unlocks

Adds an **operational rhythm** for high-volume prompts: batching, prompt fidelity, integrity passes, and anti-drift guardrails under deadline pressure—without changing the underlying integrity contract.

## Lane context

**[chaperone.]** secondaries season cadence layered on **`bounded-integrity-admissions-coaching`**; pairs with ingest skills when structured Notion state must stay aligned with drafts.

## Broader applications

- Rolling admissions cycles in any field with many near-duplicate prompts.
- Support desks answering repetitive questionnaires with per-item traceability.
- Creative agencies with burst workloads that still need QC gates per batch.

## When to use

- Operator is in **many-prompts / short-clock** mode (secondaries season, rolling deadlines).
- Need a **repeatable rhythm** without collapsing into generic essay soup.

## Principles

1. **Prompt fidelity first** — each answer maps to **that school’s actual question**; no recycled paragraphs that dodge constraints.
2. **Batching with a ledger** — track which prompts are drafted, resting, or sent for human review (Notion row or table when shipped).
3. **Integrity pass per batch** — explicit “what we are claiming vs what is verified” before polish.
4. **Rest and scope** — split unrelated schools into separate connector entries; one primary ask per thread slice.

## What not to automate away

- Program-specific **integrity rules** and **format limits** (char counts, forbidden topics) stay **human-gated** unless the repo ships automated linters.
- **Voice** belongs to the applicant; the agent supplies structure and challenge questions, not replacement personality.

## Relationship to doctrine

Thin **operational** layer on top of **`bounded-integrity-admissions-coaching`** — same integrity contract, different **cadence**.

## Docs

- **`docs/PRODUCT_DOCTRINE.md`** — med lane notes + roadmap honesty.
- **`docs/CONNECTOR_DIALOGUE_THREAD.md`** — scoped “blitz week” directives with verification.

## Cross-skill

- **`bounded-integrity-admissions-coaching`** — boundaries and lane table.
- **`admissions-doctrine-notion-sync`** — doctrine publish (**`scripts/sync_doctrine_to_notion.sh`**).
- **`structured-gdoc-notion-application-ingest`** *(optional sibling skill)* — structured Notion ingest from Google Docs.
- **`notion-activity-counter-parity-refresh`** *(optional sibling skill)* — counter/layout parity after heavy edits.

