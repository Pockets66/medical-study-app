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
| livloest_nyfodt | Det livløse nyfødte barn | `[D]` | New PEDS flow tree. 5 terminaler (responderer / svær HIE / MAS / præmatur / opioid). caseRef→genoplivning. GZ-slides + ERC/NLS 2025. Awaiting verification. |
| neonatal_ikterus | Den gule nyfødte (neonatal ikterus) | `[D]` | New PEDS flow tree. 5 terminaler (hæmolyse / fysiologisk / ammeikterus+trivsel / konjugeret / sepsis). caseRef→ikterus. GZ-slides + DPS. Awaiting verification. |
| neonatal_resp_distress | Respiratorisk distress hos den nyfødte | `[D]` | New PEDS flow tree. 5 terminaler (RDS / TTN / MAS / pneumoni-sepsis / pneumothorax). caseRef→praematur (RDS). GZ-slides + neonatal DDX. Awaiting verification. |
| neonatal_infektion | Infektionsmistanke hos det nyfødte barn | `[D]` | New PEDS flow tree. 4 terminaler (GBS-sepsis EOS / GBS-meningitis EOS / LOS / HSV). caseRef→neonatal_infektion. GZ+RMP-slides + DPS HSV-retningslinje. Awaiting verification. |
| hjertesygdom_barn | Mistanke om hjertesygdom hos barnet | `[D]` | New PEDS flow tree. 7 terminaler (vsd / tga / tof / ductus_afh_cyanose [PA+HLHS] / coarctatio / svt / fysiologisk_mislyd). Start node = 4 præsentationsformer. caseRef→hjertebarn. HA-slides + Excel + S2018. Awaiting verification. |
| haematuri_barn | Hæmaturi hos barn | `[D]` | New PEDS flow tree. 6 terminaler (PSGN / HSP-nefrit / IgA-nefropati / UVI / urolitiase / benign isoleret mikrohæmaturi). caseRef→uvi_cakut + hsp_nefrit. PW-slides + Excel + Signe (suppl). Awaiting verification. |
| feber_barn | Det febrile barn (alvorlighedsgrad + fokusjagt) | `[D]` | New PEDS flow tree. 7 terminaler (meningokok / sepsis / otitis / pneumoni / UVI / Kawasaki / viral uden fokus). caseRefs → meningokoksepsis, uvi_cakut, febrilt_barn. Awaiting verification. |
| bevidsthedspaavirket_barn | Det bevidsthedspåvirkede barn (DDX og akut handling) | `[D]` | New PEDS flow tree. 9 terminaler (meningokok / hypoglykæmi / traume / battered / DKA / ICP-tumor / meningit / postiktal / intox). caseRefs → meningokoksepsis, battered_child, dka, hjernetumor_icp. Awaiting verification. |

---

## PEDS notes

| id | Emne | Status | Note |
|----|------|--------|------|
| peds_1 | Asfyksi og neonatal genoplivning | `[D]` | Full note, 4 tabs (Definition+årsager / Genoplivning+Apgar / HIE+køling / Prognose+sequelae). GZ-slides + ERC/NLS 2025 + Excel + S2021/S2017. Awaiting verification. |
| peds_2 | Ikterus, ernæring og trivsel | `[D]` | New note, 5 tabs (Fysiologisk / Patologisk-ukonjugeret / Konjugeret+kernicterus / Behandling / Ernæring+trivsel). GZ-slides + DPS + SST 2015 + exam (ABO/hypernatriæmi). Awaiting verification. |
| peds_3 | Præmaturitet og dens komplikationer | `[D]` | New note, 5 tabs (Definitioner+årsager / Lunger / Hjerte+CNS / Tarm+øjne / Prognose). GZ-slides + kvalitetsdatabase + Excel. Partially closes apnø/lungemodning gap. Awaiting verification. |
| peds_4 | Infektioner hos det nyfødte barn | `[D]` | New note, 5 tabs (Oversigt+klinik / GBS / HSV / Andre+LOS / Det skal I kunne). GZ+RMP-slides + DPS HSV-retningslinje + Excel + S2020. Awaiting verification. |
| peds_5 | Medfødte hjertesygdomme (CHD) | `[D]` | New note, 5 tabs (Oversigt+klassifikation / Acyanotisk / Cyanotisk / Obstruktive+ductus-afh / Behandling+mislyde+arytmier). HA-slides (dec 2025) + Excel + S2018 (VSD-Alberte) + Signe (suppl). Awaiting verification. |
| peds_6 | Nyre- og urinvejssygdomme hos børn | `[D]` | New note, 5 tabs (Nyrefunktion+AKI/CKD+HT / Nefrotisk syndrom / GN+hæmaturi+HSP / CAKUT / UVI+vandladning). PW-slides (autoritativ) + Excel + V2022 Pyelonefritis + Signe (suppl, frekvenser). Awaiting verification. |

---

## Cases (OSCE)

### PEDS
| id | Emne | Status | Note |
|----|------|--------|------|
| genoplivning | Neonatal genoplivning og asfyksi | `[D]` | New case, 6 steps. GZ Case 1+2 + S2021/S2017. Cross-linked to peds_1. Awaiting verification. |
| ikterus | Neonatal ikterus og dårlig trivsel | `[D]` | New case, 6 steps. GZ Case 4 (ABO) + Case 2 (hypernatriæmi) + ikterus-workup/kernicterus. Cross-linked to peds_2. Awaiting verification. |
| praematur | Det meget præmature barn | `[D]` | New case, 6 steps (organ for organ: lunger/hjerte/hjerne/tarm/øjne/prognose). GZ running case (GA 25+0). Cross-linked to peds_3. Awaiting verification. |
| neonatal_infektion | Neonatal infektion (GBS / HSV) | `[D]` | New case, 6 steps. GZ Case 1 (GBS-meningit) + Case 2 (HSV-encephalit) + S2020 framing. Cross-linked to peds_4. Awaiting verification. |
| hjertebarn | Hjertebarn (CHD med inkompensation) | `[D]` | New case, 6 steps. S2018 Alberte-VSD som skabelon + HA-slides + Excel. Cross-linked to peds_5. Awaiting verification. |
| uvi_cakut | UVI/pyelonefritis hos pige med CAKUT | `[D]` | New case, 6 steps. V2022 Pyelonefritis (skriftlig) som template + PW-slides UVI-block. Cross-linked to peds_6. Awaiting verification. |
| hsp_nefrit | IgA-vaskulit (HSP) med nefrit hos pige | `[D]` | New case, 6 steps. PW-slides 16-18 (autoritativ) + Signe (suppl, frekvenser). Cross-linked to peds_6 + haematuri_barn-flow (t_hsp). Awaiting verification. |
| nefrotisk_sndr | Nefrotisk syndrom hos småbarn | `[D]` | New case, 6 steps. PW-slides 13-14 + ISKDC-protokol (flagget). Klassisk MCD/SSNS-narrativ med relaps. Cross-linked to peds_6. Awaiting verification. |
| febrilt_barn | Febrilt barn uden fokus | `[D]` | New case, 6 steps. F25 stand 6 + S2017 + V2016. Placeholder caseRef to peds_7 (note not yet created). Awaiting verification. |
| meningokoksepsis | Meningokoksepsis med petekkier | `[D]` | New case, 6 steps. F23 stand 6. Placeholder caseRef to peds_7. Awaiting verification. |
| astma_atopi | Astma + atopisk dermatit | `[D]` | New case, 6 steps. E23 stand 6 + S2021 skriftlig. Placeholder caseRef to peds_8. Awaiting verification. |
| dka | Diabetisk ketoacidose | `[D]` | New case, 6 steps. E23 stand 3 + V2020. Placeholder caseRef to peds_9. Awaiting verification. |
| nyopdaget_t1d | Nyopdaget T1D uden DKA | `[D]` | New case, 6 steps. E24 stand 4. Placeholder caseRef to peds_9. Awaiting verification. |
| hjernetumor_icp | Krampende barn → hjernetumor/ICP | `[D]` | New case, 6 steps. E24 stand 7. Placeholder caseRef to peds_10. Awaiting verification. |
| pubertas_praecox | Pubertas præcox | `[D]` | New case, 6 steps. F25 stand 4. Placeholder caseRef to peds_9. Awaiting verification. |
| coeliaki_vaekst | Lav højde → cøliaki | `[D]` | New case, 6 steps. F23 stand 7. Placeholder caseRef to peds_11. Awaiting verification. |
| battered_child | Mistanke om børnemishandling | `[D]` | New case, 6 steps. F24 stand 3. Placeholder caseRef to peds_12. Awaiting verification. |
| funktionelle_mavesmerter | Funktionelle mavesmerter | `[D]` | New case, 6 steps. F24 stand 1. Placeholder caseRef to peds_11. Awaiting verification. |

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

### PEDS
- [ ] obs_10 — slim to intrauterin/intrapartal asfyksi only (CTG-mønstre, STAN,
      scalp-pH) now that neonatal content lives in peds_1. Needs OBS CTG slides.
- [ ] Standalone apnø/bradykardi + detaljeret antenatal håndtering (kun delvist
      dækket i peds_3) — udvid hvis eksamenssæt kræver mere.

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
| 2026-06-01 | ui | Complete case↔note linking — caseRefs on all notes + "Relaterede noter" bars on all cases |
| 2026-06-03 | peds_1 | New note — Asfyksi/neonatal genoplivning from GZ-slides (authoritative). First populated PEDS note; replaces stub. |
| 2026-06-03 | case:genoplivning | New PEDS case + Pædiatri section in Cases tab + .badge-paed; cross-linked to peds_1. |
| 2026-06-03 | flow:livloest_nyfodt + schema | New PEDS flow tree; flowData.spec += PEDS + buildFlowPicker PEDS badge; data-model.md updated. |
| 2026-06-03 | peds_2 | New note — Ikterus/ernæring/trivsel from GZ-slides (authoritative). Second PEDS note. |
| 2026-06-03 | case:ikterus | New PEDS case (ikterus/trivsel); cross-linked to peds_2. |
| 2026-06-03 | flow:neonatal_ikterus | New PEDS flow tree (timing + konjugering); caseRef→ikterus. |
| 2026-06-11 | peds_3 | New note — Præmaturitet from GZ-slides (authoritative). Third PEDS note; folds in caffein (apnø) + antenatal steroid (lungemodning). |
| 2026-06-11 | case:praematur | New PEDS case (organ-by-organ præmaturitet); cross-linked to peds_3. |
| 2026-06-11 | flow:neonatal_resp_distress | New PEDS flow tree (neonatal respiratorisk distress); RDS→praematur case. |
| 2026-06-11 | peds_4 | New note — Infektioner hos det nyfødte barn (GBS + HSV + LOS) from GZ+RMP-slides (authoritative). Fourth PEDS note. |
| 2026-06-11 | case:neonatal_infektion | New PEDS case (GBS + HSV); Pædiatri-card spliced; cross-linked to peds_4. |
| 2026-06-11 | flow:neonatal_infektion | New PEDS flow tree (infektionsmistanke); 4 terminaler; caseRef→neonatal_infektion. |
| 2026-06-11 | peds_5 | New note — Medfødte hjertesygdomme (CHD) fra HA-slides (autoritativ) + Excel + S2018. Femte PEDS note; dækker pink/blue/ductus-afh/obstruktive + ABCD + prostaglandin + mislyde + SVT. |
| 2026-06-11 | case:hjertebarn | New PEDS case (S2018 Alberte-VSD); Pædiatri-card spliced; cross-linked to peds_5. |
| 2026-06-11 | flow:hjertesygdom_barn | New PEDS flow tree (mistanke om hjertesygdom); 7 terminaler omkring de 4 præsentationsformer; vsd-terminal → case hjertebarn. |
| 2026-06-12 | peds_6 | New note — Nyre- og urinvejssygdomme hos børn fra PW-slides (autoritativ) + Excel + V2022. Sjette PEDS note; dækker nyrefunktion/AKI/CKD/HT, nefrotisk syndrom, GN+HSP+hæmaturi, CAKUT-spektret, UVI+vandladning. |
| 2026-06-12 | case:uvi_cakut | New PEDS case (UVI/pyelonefritis hos 8-årig pige med CAKUT, modelleret efter V2022 Pyelonefritis skriftlig); Pædiatri-card spliced; cross-linked to peds_6. |
| 2026-06-12 | flow:haematuri_barn | New PEDS flow tree (hæmaturi-DDX); 6 terminaler; caseRef→uvi_cakut. Lukker tab 3 (GN/hæmaturi) i peds_6 ind i en symptomudredning. |
| 2026-06-12 | case:hsp_nefrit | New PEDS case (IgA-vaskulit med nefrit, klassisk PW-slide-narrativ); cross-linked to peds_6 + haematuri_barn t_hsp. |
| 2026-06-12 | case:nefrotisk_sndr | New PEDS case (idiopatisk nefrotisk syndrom hos 3-årig dreng; MCD-præsentation; ISKDC-prednisolon; relaps); Pædiatri-card spliced; cross-linked to peds_6. |
| 2026-06-13 | cases:peds (10 new) | Ten new PEDS cases covering F23-F25 + E23-E24 + målbeskrivelse. peds_7..peds_12 are placeholder caseRefs (notes follow in separate task). |
| 2026-06-13 | flow:feber_barn | New PEDS flow tree (Task 26 batch 1). 7 terminaler; cross-links to meningokoksepsis + uvi_cakut + febrilt_barn. |
| 2026-06-13 | flow:bevidsthedspaavirket_barn | New PEDS flow tree (Task 26 batch 1). 9 terminaler; cross-links to meningokoksepsis + dka + hjernetumor_icp + battered_child. Shares t_meningokok with feber_barn (cross-pollination intentional). |
