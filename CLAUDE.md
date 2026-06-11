# CLAUDE.md — K8 Studieguide

Guidance for Claude (Claude Code in VS, and the brainstorming Claude in claude.ai)
working on this project. Read this before touching anything.

---

## What this is

A single-file HTML study app for the **K8** exam — Danish obstetrics,
gynaecology and paediatrics. Everything lives in **`index.html`**: vanilla JS,
inline data arrays, no build step, no framework, no dependencies beyond Google
Fonts. It is meant to be opened directly in a browser and to load instantly.

All user-facing content is in **Danish**. Code, comments and docs are in English.

### The three content pillars

The whole point of the app is that these three views of the same material are
**cross-linked**, so studying any one of them jumps you to the others:

1. **Pensum** — reference notes, organised by topic/diagnose (`gyn_6`, `obs_1`…).
   Tabbed cards. This is the "textbook" layer.
2. **Symptomudredning (Flow-diagnostik)** — interactive diagnostic trees
   organised by **presenting symptom**, not by diagnosis. They mirror the
   deductive reasoning used in cases: ask → find → branch → tentativ diagnose +
   differentialer + behandling + prognose. One symptom fans out across many
   diagnoses.
3. **Cases** — OSCE-style step-by-step cases with a click-to-reveal mechanic.

**The linking is the goal, not a nice-to-have.** A note lists its related
cases; a case links back to its notes; a flow tree's terminal nodes link to the
matching note tab and case. When you add content to one pillar, wire it to the
others.

---

## Sourcing hierarchy (non-negotiable)

When content conflicts, the higher source wins. Always:

1. **Lecture slides** — authoritative. The curriculum follows these.
2. **Exam sets** (eksamenssæt / rettearker) — what actually gets tested; use for
   emphasis, framing, and traps.
3. **Signe's notes** — supplementary only. They are a few years old and the
   curriculum has changed; use them to fill gaps, never to override a slide.

If a slide and a note disagree, the slide is right and the note is stale. When
you make a sourcing call, note it in the task file so it can be reviewed.

Other content rules:
- **No emojis in the UI.** (Docs/markdown may use them; the app must not.)
- Pitch detail at **exam level** — keep the clinical logic, drop material the
  slides themselves flag as "ikke pensum" (e.g. radioterapi-doser, molekylær
  post-op stratificering) unless asked.

---

## How work is executed

The loop is: **brainstorm in claude.ai → write a task → run it in Claude Code →
commit & push → GitHub syncs.**

1. **Brainstorm & cross-check in the claude.ai chat.** Extract the slides, map
   them against the Excel exam notes, flag conflicts and open questions, get the
   owner's decisions.
2. **Write the task as two files** (see below).
3. **Execute in Claude Code (VS).** The owner runs `claude "Read
   tasks/NN_topic.md and implement it"`.
4. **Commit & push.** The GitHub integration auto-syncs the repo into the Claude
   project knowledge.

> **`index.html` is read from the GitHub-synced project knowledge, never from
> local disk.** Do not look for it on disk or assume a local copy. The synced
> state is the source of truth.

### The two-document task format

Every content/feature change is a pair of files in `tasks/`:

- **`NN_topic.md`** — the instruction file. Always four sections:
  1. **Context** — what, why, sources, dependencies, and any baked-in decisions.
  2. **Implementation** — exact `find`/`replace` anchors or Python splice blocks,
     guarded with `assert`s that fail loudly rather than corrupt the file.
  3. **roadmap.md update** — the status row change + a commit-log line.
  4. **What to test** — a browser checklist.
- **`NN_topic_data.js`** — the bare data object(s) to splice in (no wrapper).

`NN` is sequential across the whole project. Task files are **deleted** after
they're executed (a step in the task itself).

### Status flow

Tracked in `docs/roadmap.md`:

| Symbol | Meaning |
|--------|---------|
| `[ ]` | Planned |
| `[~]` | In progress (being drafted in chat) |
| `[D]` | Drafted — written, awaiting medical review |
| `[V]` | Verified — medically approved by the owner |
| `[✓]` | Committed — merged into `index.html` |

**Nothing reaches `[✓]` without passing through `[V]` first.** New or rewritten
content lands at `[D]`; the owner reviews against the slides and flips it to
`[V]`.

---

## Data model (summary — see `docs/data-model.md` for the authority)

Inline arrays in `index.html`: `notesData`, `casesData`, `flowData`.

**Note (Pensum):**
```js
{ id:'gyn_6', spec:'GYN', num:6, title:'...',
  src:'...sources...',
  sub:'<table class="nst">...</table>',   // quick-reference summary
  tabs:[ { label:'...', grid:[ {l:'label', c:'<html>', full?, hl?, warn?} ] } ],
  caseRefs:['...']                         // bidirectional case links
}
```
- A note renders as flat grid if `tabs` is absent, tabbed if present.
- Card flags: `full` (full-width), `hl` (highlighted — used for klinisk perler),
  `warn` (amber — used for CAVE/cautions).
- `spec` ∈ `GYN` · `OBS` · `PEDS`. Spec key convention is `'PEDS'` (matching
  spoken usage), mapped to the `--paed` / `--paed-bg` CSS variables.

**Cases** use a `steps[]` reveal model. **Flow** uses a node/edge tree.

> **Any schema change must update `docs/data-model.md` in the same commit.**

---

## Repo layout

```
index.html              # the whole app — synced from GitHub, not edited on disk
docs/
  CLAUDE.md             # this file
  data-model.md         # authoritative schema reference
  roadmap.md            # status of every note/case/flow + commit log + backlog
tasks/                  # NN_topic.md + NN_topic_data.js pairs (deleted after run)
reference/              # READ-ONLY source HTML; never modify
```

---

## Current shape & near-term

- GYN notes `gyn_1…gyn_9` and OBS notes `obs_1…obs_10` exist; PEDS is scaffolded
  and awaiting verified content.
- **Task 15** (flow-diagnostik ↔ note/case linking) is deliberately deferred —
  batch it once more flow trees exist rather than wiring two in isolation.
- Ongoing: populate PEDS, and keep extending the three pillars + their links as
  new slides are verified.
