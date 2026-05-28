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
| gyn_1 | Antikonception og abort | `[✓]` | Prescribing workflow + generation comparison thin — minor revision planned |
| gyn_2 | Blødningsforstyrrelser og PCOS | `[✓]` | Blødningsskema + PCOS follow-up (HbA1c, metabolisk syndrom) thin |
| gyn_3 | Endometriose og godartede tumorer | `[✓]` | Fibrom-subtyper + adenomyose missing — low priority |
| gyn_4 | Uro-gynækologi | `[✓]` | TVT + prolaps-grading missing |
| gyn_5 | Tidlige graviditetskomplikationer | `[✓]` | Mola hydatidosa thin |
| gyn_6 | Gynækologisk cancer | `[✓]` | ⚠️ Ovariecancer næsten ikke dækket — needs forelæsning upload |
| gyn_7 | Underlivsinfektion og PID | `[D]` | Converted to sub-tabs (PID / Klamydia / Gonore / Bakteriel vaginose / Candida). Awaiting medical verification. |
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
