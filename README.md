# AGI — The Autonomous Gibsey Index

AGI is the **indexing + navigation engine** for *Gibsey*'s QDPI symbol system.

If a normal book is "page 1 → page 2 → page 3," AGI treats reading as a **path through a graph**, where a reader's journey is a **trace** (a replayable "program") made of symbol-tokens and the pages they point to.

This repo exists so we can stop re-explaining the system from scratch and instead work from **first principles ("laws")** and **stable naming conventions**.

---

## Core idea in one sentence

**QDPI glyphs are a numbering/address system; AGI is the runtime that turns those addresses into a navigable, generative reading path.**

---

## Vocabulary

### QDPI modes (the "four directions")

We use four modes everywhere:

- **Q** — Queue (canonical pages; the book-as-written)
- **M** — Monologue (generated interstitial pages; usually "Q→M→Q" bridges)
- **D** — Dialogue (reader query → character response pages)
- **H** — Holologue (cross-voice/cross-section interjections and portals)

> Note: the NU-256 HTML grid labels the base mode as **P** ("Primary").  
> In AGI we rename that to **Q** ("Queue") to emphasize **canon order / queue of pages** (not "most important").  
> So: **P in the grid == Q in AGI**.

### Canon pages vs AGI trace (two coordinate systems)

There are two coordinate systems that must never be confused:

1. **Canon page id**: the novel's linear order (1–710).  
   We reference these as `Q001 … Q710` (canon pages are Queue pages).

2. **AGI trace**: the reader's path ("what happened"), recorded as a sequence of **visited page-states** and/or **clicked bonds** (see "Traces").

### Page badges vs Bond/Prompt badges (critical distinction)

AGI has two kinds of "symbol display," and mixing them up causes most confusion:

- **Page badge**: what the current page *is* (a Q page, M page, D page, or H page).
- **Bond/Prompt badge**: what action is available *from here* (Q→M, M→Q, Q→H, etc.).

In early demos we intentionally keep the **bond badge vocabulary** small and stable, even if page badges become richer later.

### Page badge rule (explicit)

This is how pages should be visually badged:

- **Canon Q pages**: page badge = the section's **Q glyph** (grid "P/Q"), upright (0°).
- **Generated M pages**: page badge = the section's **M glyph** (grid "M"), upright (0°).
- **Generated H pages**: page badge = the section's **H glyph** (grid "H"), upright (0°).
- **Generated D pages**: page badge = the section's **D glyph** (grid "D"), upright (0°).

Bond/prompt badges are separate and can be a reduced vocabulary (see milestones).

---

## The 16 sections (canon index → character/voice)

AGI treats each section as an address-domain (a namespace). These are the canon page ranges:

### Canon table of contents (page-number ranges)

- **Section 1 (Q001–Q008)** — *an author's preface* (**an author**)
- **Section 2 (Q009–Q024)** — *London Fox Who Vertically Disintegrates* (**London Fox**)
- **Section 3 (Q025–Q203)** — *An Unexpected Disappearance: A Glyph Marrow Mystery* (**Glyph Marrow**)
- **Section 4 (Q204–Q235)** — *An Expected Appearance: A Phillip Bafflemint Noir* (**Phillip Bafflemint**)
- **Section 5 (Q236–Q307)** — *Jacklyn Variance, The Watcher, is Watched* (**Jacklyn Variance**)
- **Section 6 (Q308–Q354)** — *The Last Auteur* (**Oren Progresso**)
- **Section 7 (Q355–Q380)** — *Gibseyan Mysticism and its Symbolism* (**Old Natalie Weissman**)
- **Section 8 (Q381–Q385)** — *Princhetta Who Thinks Herself Alive* (**Princhetta**)
- **Section 9 (Q386–Q411)** — *Petition for Bankruptcy…* (**Cop-E-Right**)
- **Section 10 (Q412–Q432)** — *The Tempestuous Storm* (**New Natalie Weissman**)
- **Section 11 (Q433–Q487)** — *Arieol Owlist Who Wants to Achieve Agency* (**Arieol Owlist**)
- **Section 12 (Q488–Q500)** — *The Biggest Shit of All Time* (**Jack Parlance**)
- **Section 13 (Q501–Q564)** — *An Expected Appearance… (Ch. 4–6)* (**Manny Valentinas**)
- **Section 14 (Q565–Q641)** — *An Unexpected Disappearance… (Ch. 7–11)* (**Shamrock Stillman**)
- **Section 15 (Q642–Q677)** — *Todd Fishbone Who Dreams of Synchronistic Extraction* (**Todd Fishbone**)
- **Section 16 (Q678–Q710)** — *The Author's Preface* (**The Author**)

### Voice list (section → character)

1. an author
2. London Fox
3. Glyph Marrow
4. Phillip Bafflemint
5. Jacklyn Variance
6. Oren Progresso
7. Old Natalie Weissman
8. Princhetta
9. Cop-E-Right
10. New Natalie Weissman
11. Arieol Owlist
12. Jack Parlance
13. Manny Valentinas
14. Shamrock Stillman
15. Todd Fishbone
16. The Author

---

## The "laws" (AGI first principles)

These are spec-level constraints. If anything contradicts these, the code is wrong.

### Law 1 — Q pages are canon

`Q###` pages are the fixed, original pages in the novel's linear order.

### Law 2 — Bonds carry badges

Symbols shown under a page are **badges on bonds/prompts**, i.e. "this move is available here." They are not necessarily "the identity of the page you are on."

### Law 3 — QDPI is a move alphabet

From any moment in reading, AGI can offer moves whose *type* is in `{Q, M, D, H}`. That's the "four directions at once" feeling: it's **edge-type-first**, not geometry-first.

### Law 4 — Holologue gating is scene-based, with short-section exceptions

- In long sections, **H prompts only appear at scene exits**.
- In short sections, we allow **H prompts on any page**.

Current rule for the early demo:

- **H anywhere**: Section 1 (an author, 8 pages) + Section 8 (Princhetta, 5 pages)
- **H at scene exits**: London (16 pages) + Jacklyn (72 pages, Q236–Q307)

### Law 5 — Holologues can return or enter (QDPI-12 default is explicit)

Holologues can function as:

- a commentary interjection that returns you to where you were, or
- a portal that lets you enter the holologuer's section.

**QDPI-12 default:** every H page shows **two explicit bonds**:

- **Return** (to the next canon Q in the source stream, or next scene entry)
- **Enter** (into the holologuer's Q stream at a defined entry point)

### Law 6 — Traces are replayable artifacts

A reading session is a trace. Traces should be storable, shareable, and replayable.

---

## The 16 move types (full system)

Across the full QDPI system there are **16 transition types**:

- From **Q**: `Q→Q, Q→M, Q→D, Q→H`
- From **M**: `M→Q, M→M, M→D, M→H`
- From **D**: `D→Q, D→M, D→D, D→H`
- From **H**: `H→Q, H→M, H→D, H→H`

AGI can implement these incrementally, which is why we define "QDPI-12 / 36 / 64 / 256" as development milestones.

---

## QDPI as an address space

The NU-256 grid encodes:

**16 voices × 4 modes (Q/M/D/H) × 4 rotations = 256 glyphs**

Practical view:

```text
glyph := (voice, mode, rotation)
rotation ∈ {0°, 90°, 180°, 270°}
```

Poetic/math view:

- Rotations behave like **phase** (complex-plane intuition):
  - 0° ~ 1
  - 90° ~ i
  - 180° ~ −1
  - 270° ~ −i
- The "page number" is not just magnitude; it has **orientation**.

---

## Milestones

### QDPI-12 (starter demo: 4 voices, Q-origin bond badges)

**Goal:** ship something testable fast, with minimal bond-symbol burden, while preserving the *feel* of QDPI.

#### What's included

- Voices: **an author**, **London Fox**, **Jacklyn Variance**, **Princhetta**
- Bond badges defined only for actions offered from **Q pages**
- Rotations used for bond badges: **0°, 90°, 270°**
- Implemented moves (minimum viable):
  - `Q→Q` (continue canon)
  - `Q→M` (insert monologue bridge)
  - `Q→H` (insert holologue / portal)
  - plus navigational returns:
    - `M→Q`
    - `H→Q`

> In QDPI-12, `M→Q` and `H→Q` can be treated as **pure navigation** and omitted from the *node trace*. They can still be logged as edges/events for replayability.

#### Token naming convention (recommended)

Use short voice prefixes:

- `aa` = an author
- `lf` = London Fox
- `jv` = Jacklyn Variance
- `p` = Princhetta

QDPI-12 bond tokens (3 per voice):

- `aaq0, aaq90, aaq270`
- `lfq0, lfq90, lfq270`
- `jvq0, jvq90, jvq270`
- `pq0, pq90, pq270`

Interpretation (QDPI-12 bond badges):

- `*q0` = Q→Q (continue within canon stream)
- `*q90` = Q→M (spawn a monologue from a Q page)
- `*q270` = Q→H (spawn a holologue from a Q page)

---

### QDPI-36 (4 voices, no Dialogue, origin-aware M/H bond badges)

QDPI-36 is the next clean step once QDPI-12 works.

**Why it exists:** leaving an M page (or an H page) has different semantics than leaving a Q page, and QDPI-12 can't express that cleanly.

#### What's included

- Same 4 voices
- Modes used for bond families: **Q, M, H** (Dialogue removed)
- Rotations used: **0°, 90°, 270°**
- Total bond tokens: `4 voices × (3 mode families) × (3 rotations) = 36`

Tokens (9 per voice):

- `aa{q,m,h}{0,90,270}`
- `lf{q,m,h}{0,90,270}`
- `jv{q,m,h}{0,90,270}`
- `p{q,m,h}{0,90,270}`

Recommended interpretation (bond badges):

- On Q pages:
  - `q0` = Q→Q
  - `q90` = Q→M
  - `q270` = Q→H
- On M pages:
  - `m0` = M→Q
  - `m90` = M→M
  - `m270` = M→H
- On H pages:
  - `h0` = H→Q
  - `h90` = H→M
  - `h270` = H→H (the "true holologue"; can reference the full AGI trace state)

---

### QDPI-64 (4 voices, complete symbol space for those voices)

This is "QDPI-256, but only for the four demo voices":

- 4 voices × 4 modes (Q/M/D/H) × 4 rotations = **64 glyphs**

You may still implement only a subset of move types at first, but the **symbol system** is complete for those voices.

---

### QDPI-256 (full book)

The full system for the full book:

- 16 voices × 4 modes × 4 rotations = **256 glyphs**
- Canonical symbol source: `qdpi/nu-256-grid.html`

---

## Known scenes (demo)

### London Fox (Q009–Q024)

- `lf_s1`: Q009–Q010 (exit: Q010)
- `lf_s2`: Q011–Q013 (exit: Q013)
- `lf_s3`: Q014–Q019 (exit: Q019)
- `lf_s4`: Q020–Q024 (exit: Q024)

### Jacklyn Variance (Q236–Q307) — first-pass gates

This is the already-established 4-part segmentation, encoded as scenes with exit markers:

- `jv_s1`: Q236–Q242 (exit: Q242)
- `jv_s2`: Q243–Q271 (exit: Q271)
- `jv_s3`: Q272–Q273 (exit: Q273)
- `jv_s4`: Q274–Q307 (exit: Q307)

(We can later refine the long cluster `jv_s2` into smaller internal "rooms" without breaking the contract.)

---

## Scene system (for H gating)

Long sections need explicit entrance/exit points so holologues don't become noise.

AGI represents scenes as ranges of canon pages with one or more exit markers:

```yaml
scenes:
  london_fox:
    - id: lf_s1
      start: Q009
      end: Q010
      exits: [Q010]
    - id: lf_s2
      start: Q011
      end: Q013
      exits: [Q013]
    - id: lf_s3
      start: Q014
      end: Q019
      exits: [Q019]
    - id: lf_s4
      start: Q020
      end: Q024
      exits: [Q024]

  jacklyn_variance:
    - id: jv_s1
      start: Q236
      end: Q242
      exits: [Q242]
    - id: jv_s2
      start: Q243
      end: Q271
      exits: [Q271]
    - id: jv_s3
      start: Q272
      end: Q273
      exits: [Q273]
    - id: jv_s4
      start: Q274
      end: Q307
      exits: [Q307]
```

Rule: H prompts appear only when `page_id ∈ exits`, except in short sections (Law 4).

---

## Traces (what AGI records)

AGI can record two complementary traces:

1. **Node trace** (visited page-states)
   - Example: `aaq0 → aaq90 → aaq0 → jvq270 → jvq0 → ...`
   - This captures what pages/artifacts were actually visited.

2. **Edge/event trace** (clicked bonds)
   - Example: `Q→M, M→Q, Q→H, H→Q, ...`
   - This captures how traversal happened (proof/replay).

QDPI-12 implementation may store only the edge/event trace (node trace is derivable). This reduces surface area for the first demo.

---

## Content generation strategy (QDPI-12)

QDPI-12 can be shipped without live generation.

- **M pages**: may start as handwritten stubs / fixture files (per gap or per scene), to test navigation + trace.
- **H pages**: may start as handwritten stubs / fixture files, to test portal semantics ("Return" vs "Enter").
- Once navigation is stable, swap in DSPy/LLM generation without changing AGI rules.

---

## Run-plan patterns (generation schedules)

AGI must generate run plans from simple inputs: ordered Q nodes + scene exit markers.

### Monologue bridges (Q→M→Q)

For a section with ordered canon pages `Q[a..b]`, for each `i` in `[a .. b-1]` generate a monologue bridge:

- Context: `Q[a..i]` (prefix-of-section)
- Output: `M_i`
- Landing: `Q[i+1]`

Chain form:

```text
Q[a]/Q[a+1]/.../Q[i]/M_i/Q[i+1]
```

Later we can optionally cap context by prefix-of-scene for long sections to control size.

### Holologue portals (Q→H→Q)

At a scene exit page `Qexit`:

- Generate `H(Qexit → Qtgt)` where `Qtgt` is chosen from candidate targets
- Then offer:
  - Return to next page in current stream, and/or
  - Enter the target stream at a chosen entry page

---

## Symbol source of truth

The canonical glyph set is the NU-256 HTML grid:

- `qdpi/nu-256-grid.html` (inline SVG, grouped by twin-pairs and strand)

The grid currently labels the base column as P; in AGI we interpret that as Q.

Implementation note: each SVG contains a `<g class="rotatable" ...>` so rotations can be applied consistently at runtime.

---

## Suggested repo structure (lightweight, but scalable)

```text
agi/
  README.md

  qdpi/
    nu-256-grid.html
    extract_symbols.py        # optional: parse HTML → JSON/SVG assets
    symbols.json              # optional: canonical registry {voice, mode, rot} → svg

  agi/
    trace.py                  # trace model + serializer
    runplan.py                # run-plan generator from Q lists + scene exits
    navigation.py             # bond/prompt generation rules

  demos/
    qdpi12/                   # minimal 4-voice demo
```

---

## What "done" means for the first sprint (QDPI-12)

1. **Canon content wired**
   - Section 1: Q001–Q008
   - Section 2: Q009–Q024
   - Section 5: Q236–Q307
   - Section 8: Q381–Q385

2. **Bonds render under Q pages**
   - `Q→Q` bond (continue)
   - `Q→M` bond (spawn monologue)
   - `Q→H` bond (spawn holologue)

3. **Monologues function**
   - `Q→M→Q` bridges work across:
     - an author (8 pages)
     - London Fox (16 pages)

4. **Holologues function**
   - Offered:
     - anywhere for an author + Princhetta
     - only at scene exits for London + Jacklyn
   - Every H page offers Return and Enter bonds (Law 5 default)

5. **AGI trace records the journey**
   - edge/event trace at minimum (node trace derivable)
   - trace can be serialized, replayed, and compared
