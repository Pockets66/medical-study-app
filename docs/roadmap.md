# K8 Studieguide — Content Roadmap

Tracks the status of every note card in `notesData`.

## Status legend

| Symbol | Meaning |
|--------|---------|
| `[ ]` | Planned — not started |
| `[~]` | In progress — being drafted in chat |
| `[V]` | Drafted — written, awaiting medical review |
| `[V]` | Verified — medically approved by owner |
| `[✓]` | Committed — merged into index.html |

> Rule: nothing moves to `[✓]` without passing through `[V]` first.

---

## GYN notes

| ID | Title | Status | Notes |
|----|-------|--------|-------|
| gyn_1 | Antikonception og abort | `[V]` | Expanded to 3 tabs: Antikonception / Abort / Nødprævention. Verified by owner. |
| gyn_2 | Blødningsforstyrrelser (AUB) | `[V]` | Full rewrite from AUB slides. 5 tabs: Oversigt / PALM / COEIN / Diagnostik / Behandling. Verified by owner. |
| gyn_3 | Endometriose og godartede tumorer | `[D]` | Full rewrite. 5 tabs: Endometriose / Adenomyose / Polypper+Fibromer / Ovariecyster / DDX akutte smerter. Awaiting verification. |
| gyn_4 | Uro-gynækologi | `[V]` | Full rewrite. 4 tabs: Udredning / Stressinkontinens / Urgeinkontinens / Genital prolaps. Verified by owner. |
| gyn_5 | Tidlige graviditetskomplikationer | `[V]` | Full rewrite. 5 tabs: Normal grav / Abortus / Retineret væv / EUG / Mola. Slides + Signe. Verified by owner. |
| gyn_6 | Gynækologisk cancer | `[D]` | Full rewrite. 5 tabs: Onkogenetik / Cervix-dysplasi+screening / Cervixcancer / Endometrie+atypi / Ovariecancer. 2026 slides + Excel. Awaiting verification. |
| gyn_7  | Underlivsinfektion            | `[V]` | Split from gyn_7b. Tabs: BV / Bartholinitis / PID / TOA. Slides-sourced. Verified by owner. |
| gyn_7b | Seksuelt overførte infektioner | `[V]` | New note. Tabs: Herpes / HPV / Klamydia / Gonore / Syfilis / Mycoplasma. Slides-sourced. Verified by owner. |
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

## Symptomudredning — diagnostiske flowcharts (flowData)

| ID | Symptom | Status | Notes |
|----|---------|--------|-------|
| bloedningsforstyrrelser | Blødningsforstyrrelser (abnorm uterin blødning) | `[D]` | Grounded in gyn_2 (AUB/PALM-COEIN), gyn_6 (cancer) + bloedning/cancer cases. Awaiting owner review. |
| akut_underlivssmerter | Akutte smerter i underlivet | `[V]` | Verified vs in-app gyn_3/5/7 + cases. Folsyre-under-MTX confirmed as slide typo (excluded); hCG-endepunkt `<2` confirmed. |

### PEDS (Pædiatri)
| id | Emne | Status | Note |
|----|------|--------|------|
| peds_1 | (stub) | `[ ]` | Placeholder note — scaffolding only, no content yet |

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
| 2026-05-29 | gyn_1 | Patch: Blanket A udgået, SST-generationsvejledning, VTE-tabel, succesrater abort, spiral/sterilisation tilføjet |
| 2026-05-29 | gyn_5 | Full rewrite — 2026 slides, rescue progesteron, mola protokol, anti-D, MTX ventetid |
| 2026-05-29 | gyn_4 | Full rewrite — 2026 slides, TVT-kriterier, prolaps-gradering, mirabegron, pessar-algoritme |
| 2026-05-29 | flow:akut_underlivssmerter | New feature — Symptomudredning tab + flow renderer; first tree (EUG/abort/PID/torsion/cyste/endometriose/appendicit) |
| 2026-05-31 | flow:bloedningsforstyrrelser | New flow tree (PMB/cancer, graviditet, cervix, fibrom, PCOS, koagulopati, HMB); folded in everything-except-cancer → [V] |
| 2026-05-31 | gyn_3 | Full rewrite — 2026 slides, IOTA B/M regler, Ryeqo, UAE statistik, akutte underlivssmerter DDX |
| 2026-06-01 | gyn_6 | Full rewrite — onkogenetik (HBOC/Lynch/Knudson/RRBSO), cervix dysplasi+screening, cervix/endometrie/ovarie cancer from 2026 slides |
| 2026-06-01 | ui | Nav refactor → Pensum/Flow-diagnostik/Cases/Tips; fix page-1 tab bug; consolidate Hyppighed/Studiestrategi/Eksamenstips under Tips sub-tabs |
| 2026-06-01 | ui | Collapsible Pensum groups (GYN/OBS/PEDS); add PEDS spec + colour handling + empty group + peds_1 stub |
