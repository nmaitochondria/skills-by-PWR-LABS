# Notion Activity Page Layout

Canonical activity pages use two toggleable Heading 1 sections, modeled on the Badri **Learning Assistant — LS 7A/7C and Chem 14BE** row.

## Limit line (drives counter coloring)

Each counter region starts with a single paragraph:

- **`word / character limit: <n> characters`** → **character** line shows padded `current character count: cur/limit` in **green/red** vs `<n>`. **Word** line shows `current word count: ` + **natural** decimal (e.g. `108`, not zero-padded)—reference only, no color.
- **`word / character limit: <n> words`** → **word** line is colored `cur/limit` vs `<n>`; **character** line is natural decimal count only.

There is no live Notion formula for “flip limit type”; changing the limit line and re-running **`refresh_activity_counts.py --rewrite-layout`** (or re-import) is the supported way to switch behavior.

## Section 1 — `experience description`

- divider
- `word / character limit: 700 characters`
- divider
- `current word count:` + natural decimal (reference only when limit is **characters**)
- `current character count:` + padded `chars/700` (green/red)
- to-do: `refresh word count`
- **divider** (starts the narrative region counted for refresh / stamped counters)
- narrative paragraph(s) (this body is what `desc` / `_rich_paragraphs` use; word and character counts are computed from the same string)
- **divider** (nested full-width rule closing the experience text block—always present so the next toggle does not visually merge)

## Section 2 — `most meaningful remarks`

- paragraph `if applicable` (where used)
- divider
- `word / character limit: 1325 characters`
- divider
- same counter pattern vs **1325**
- to-do: `refresh word count`
- divider, narrative (or N/A stub), closing divider

## Materials (flat PS / secondary essay pages)

Same counter helper (`_counter_controls`) with `primary="characters"` for PS (`word / character limit: 5300 characters`) and `primary="words"` for the secondary template (`word / character limit: 500 words` by default—tune `DEFAULT_SECONDARY_WORD_LIMIT` in code or rebuild after editing the template limit in Notion).

**Master materials database** (templates for all future students):  
https://www.notion.so/35d50bc77832808591cbd498254d55b7?v=35d50bc77832805196bf000c41fd4635  
Update named templates via `scripts/sync_materials_templates.py` (uses `data_sources.list_templates` on that DB).

## Refresh / extraction noise

`_is_noise` in `refresh_activity_counts.py` must exclude: `word / character limit:`, legacy `character limit:`, counter lines, to-do label, N/A stub, `if applicable`. If the limit line is mistaken for narrative, word and character totals will be wrong (extra tokens inflate the word line).

## Verification checklist

- Every expected row has a non-empty description unless the source doc is empty.
- Starred AMCAS rows have non-empty most-meaningful text when applicable.
- Counter values match extracted narrative only (limit lines never inside `desc` / `mm` strings).
- Both Badri surfaces can exist: document-review `activities + experiences` and application-tracker copy—keep them consistent unless the operator scopes to one.
