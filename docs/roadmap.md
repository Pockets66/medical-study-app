# K8 Studieguide — Content Roadmap

Tracks the status of every note card in `notesData`.

## Status legend

| Symbol | Meaning |
|--------|---------|
| `[ ]` | Planned — not started |
| `[~]` | In progress — being drafted in chat |
| `[D]` | Drafted — written, awaiting medical review |
| `[V]` | Verified — medically approved by owner |
| `[✓]` | Committed — merged into index.html |

> Rule: nothing moves to `[✓]` without passing through `[V]` first.

---

## GYN notes

| ID | Title | Status | Notes |
|----|-------|--------|-------|
| gyn_1 | Antikonception og abort | `[D]` | Expanded to 3 tabs: Antikonception / Abort / Nødprævention. Awaiting medical verification. |
| gyn_2 | Blødningsforstyrrelser (AUB) | `[D]` | Full rewrite from AUB slides. 5 tabs: Oversigt / PALM / COEIN / Diagnostik / Behandling. Awaiting verification. |
| gyn_3 | Endometriose og godartede tumorer | `[✓]` | Fibrom-subtyper + adenomyose missing — low priority |
| gyn_4 | Uro-gynækologi | `[✓]` | TVT + prolaps-grading missing |
| gyn_5 | Tidlige graviditetskomplikationer | `[✓]` | Mola hydatidosa thin |
| gyn_6 | Gynækologisk cancer | `[✓]` | ⚠️ Ovariecancer næsten ikke dækket — needs forelæsning upload |
| gyn_7  | Underlivsinfektion            | `[D]` | Split from gyn_7b. Tabs: BV / Bartholinitis / PID / TOA. Slides-sourced. Awaiting verification. |
| gyn_7b | Seksuelt overførte infektioner | `[D]` | New note. Tabs: Herpes / HPV / Klamydia / Gonore / Syfilis / Mycoplasma. Slides-sourced. Awaiting verification. |
| gyn_8 | Human reproduktion | `[✓]` | AMH mangler — low priority |
| gyn_9 | Hormonbehandling i postklimakteriet | `[✓]` | ⚠️ Systemisk MHT ikke dækket — needs forelæsning/eksamenssæt upload |

---

## OBS notes

| ID | Title | Status | Notes |
|----|-------|--------|-------|
| obs_1 | Præeklampsi / HELLP | `[✓]` | Review MgSO4-protokol og svær PE-kriterier mod Signes noter |
| obs_2 | Svangreomsorg og graviditetsundersøgelse | `[✓]` | — |
| obs_3 | Føtalmedicin og prænatal diagnostik | `[✓]` | — |
| obs_4 | Tvillingegraviditet | `[✓]` | TTTS/TAPS detaljer thin |
| obs_5 | Væksthæmning og blødning | `[✓]` | — |
| obs_6 | GDM og medicinske sygdomme | `[✓]` | Astma, epilepsi, hjertelidelse i graviditet ikke dækket |
| obs_7 | Præterm fødsel | `[✓]` | — |
| obs_8 | Barselskomplikationer | `[✓]` | — |
| obs_9 | Virussygdomme under graviditet | `[✓]` | ⚠️ CMV, rubella, varicella ikke dækket — needs upload |
| obs_10 | Asfyksi og neonatal genoplivning | `[✓]` | ⚠️ CTG-mønstre intrapartalt ikke dækket — needs upload |

---

## Backlog — topics not yet in the app

Topics identified from exam sets or målbeskrivelser that have no note card yet.

### GYN
| Topic | Priority | Source | Blocker |
|-------|----------|--------|---------|
| Ovariecancer (dedikeret note) | 🔴 High | Signe noter + mangler forelæsning | Upload forelæsning |
| Cervixscreening / HPV / CIN-pathway | 🔴 High | Signe noter + eksamenssæt | Kan draftes nu |
| Klimakteriet (bredere end MHT) | 🟡 Medium | Mangler eksamenssæt | Upload eksamenssæt |
| Inkontinens (uddybet selvstændig note) | 🟡 Medium | Signe noter | Kan draftes nu |

### OBS
| Topic | Priority | Source | Blocker |
|-------|----------|--------|---------|
| Den normale fødsel / dystoci | 🔴 High | Eksamenssæt F25, S2018 | Kan draftes nu |
| CTG-tolkning | 🔴 High | Mangler forelæsning | Upload forelæsning |
| Flerfoldsgraviditet (uddybet) | 🟡 Medium | Signe noter | Kan draftes nu |

---

## Upload wishlist

Files that would unlock blocked topics:

- [ ] Forelæsning: ovariecancer
- [ ] Forelæsning: CTG-tolkning / intrapartum overvågning
- [ ] Forelæsning eller eksamenssæt: klimakteriet / MHT
- [ ] Eksamenssæt specifikt om PID / kønssygdomme (hvis det findes)
- [ ] Forelæsning: virussygdomme i graviditet (CMV, rubella, varicella)

---

## Commit log

| Date | ID | Change |
|------|----|--------|
| 2026-05-28 | gyn_7 | Rewrote PID note — full ætiologi, 4/5 kriterier, AB-regimer, sequelae med tal, Fitz-Hugh-Curtis |
| 2026-05-28 | ui | Add sub-tab support to notes renderer — test case: gyn_7 |
| 2026-05-28 | ui | Add bidirectional case-note linking — noteRef + caseRefs |
| 2026-05-28 | gyn_1 | Expand antikonception note — generation guide, VTE tal, abort fordele/ulemper, nødprævention |
| 2026-05-28 | gyn_7 + gyn_7b | Split infections note — Underlivsinfektion (4 tabs) + STD (6 tabs), slides-sourced |
| 2026-05-28 | gyn_7b | Patch: remove unverified HPV % + screening ages, remove FHC from klamydia |
| 2026-05-28 | gyn_2 | Full rewrite — AUB slides, FIGO cycle values, PALM-COEIN, PCOS tabel, behandlingsreduktionsprocenter |
