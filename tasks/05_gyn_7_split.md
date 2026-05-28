# Task 05: Split gyn_7 — Underlivsinfektion og Seksuelt overførte infektioner

## Context

Task 02 introduced gyn_7 with 5 tabs mixing PID-type infections and STDs.
This task splits that into two separate notes:

- `gyn_7`  → Underlivsinfektion (BV, Bartholinitis, PID, TOA)
- `gyn_7b` → Seksuelt overførte infektioner (Herpes, HPV, Klamydia, Gonore,
  Syfilis, Mycoplasma genitalium)

Content is sourced from the lecture slides (Genitale_infektioner_K8_e2025)
and the K8 exam notes Excel. Slides take priority over all other sources.

Also updates `docs/data-model.md` to allow `num` to be a string.

---

## Implementation

### 1. Update `docs/data-model.md`

Find:
```
- **`num`**   // display number (integer)
```

Replace with:
```
- **`num`**   // display label — string or integer (e.g. 7, '7b')
```

---

### 2. File: `index.html` — replace gyn_7

Find the entire existing `gyn_7` object in `notesData`. It starts with:
```
{ id:'gyn_7',
```
and ends just before:
```
{ id:'gyn_8',
```

Replace the entire `gyn_7` object (including trailing comma) with the
following two objects:

```js
{ id:'gyn_7', spec:'GYN', num:7, title:'Underlivsinfektion',
  src:'Genitale infektioner K8 2025 (slides) + K8 eksamensnoter',
  sub:'<table class="nst"><thead><tr><th>Entitet</th><th>Ætiologi</th><th>Nøglefund</th></tr></thead><tbody><tr><td><strong>Bakteriel vaginose</strong></td><td>Floraforstyrrelse — Gardnerella + anaerobe</td><td>Amsel 3/4 · fiskelugt · pH &gt;4,5</td></tr><tr><td><strong>Bartholinitis</strong></td><td>Infektion/retention i Bartholinske kirtel</td><td>Primært yngre — biopsi hos ældre</td></tr><tr><td><strong>PID</strong></td><td>Klamydia (hyppigst), gonokokker, anaerobe</td><td>Rokkeømhed + mindst 1 af 4 øvrige kriterier</td></tr><tr><td><strong>TOA</strong></td><td>Polymikrobiel (anaerobe 50–90 %)</td><td>Abd. smerter 85 % · feber 65 % · rokkeømhed 75 %</td></tr></tbody></table>',
  tabs:[
    { label:'Bakt. vaginose', grid:[
      {l:'Definition og ætiologi', c:'Ubalance i vaginalfloraen — ikke en egentlig bakterieinfektion, men en floraforskydning. Reduktion af Lactobacillus → overvækst af Gardnerella vaginalis og anaerobe. Disponerende: skiftende partnere, hormonelle ændringer, antibiotika, svækket almentilstand.'},
      {l:'Symptomer', c:'<ul><li>50 % af kvinder er <strong>asymptomatiske</strong></li><li>Tyndt, gråligt, ildelugtende (fiskeagtigt) udflåd</li><li>Lugt forværres efter samleje (sæd hæver pH)</li><li>Moderat kløe — ingen udtalt inflammation</li></ul>'},
      {l:'Diagnose — Amsel-kriterier (3 af 4 = &gt;90 % SSH)', c:'<ol style="padding-left:16px;line-height:1.9"><li>Udflåd med karakteristisk fiskelugt</li><li>pH &gt; 4,5</li><li>Positiv amintest: fiskelugt ved tilsætning af 10 % KOH til vaginalsekret</li><li>Clue cells ved mikroskopi (pladeepitelceller dækket af bakterier)</li></ol>'},
      {l:'Behandling', c:'<ul><li>Asymptomatisk: ingen behandling nødvendig</li><li>Symptomatisk: metronidazol eller clindamycin (po eller vaginal)</li><li>Partnerbehandling ikke nødvendig</li></ul>'},
      {l:'Klinisk relevans', c:'Øget risiko for præterm fødsel og PID. Screen og behandl inden gynækologiske indgreb og ved graviditet.', full:true, hl:true}
    ]},
    { label:'Bartholinitis', grid:[
      {l:'Definition', c:'Infektion eller retentionscyste i den Bartholinske kirtel (placeret bilateralt ved introitus vaginae, kl. 4 og 8). Udskiller slim ved seksuel stimulation.'},
      {l:'Epidemiologi og ætiologi', c:'<ul><li>Ses primært hos <strong>yngre kvinder</strong></li><li>Ofte polymikrobiel — klamydia og gonokokker kan være årsag</li><li>Obs: hos <strong>ældre kvinder</strong> skal der tages biopsi for at udelukke cancer</li></ul>'},
      {l:'Symptomer og fund', c:'<ul><li>Hævelse med fluktuation ved labia / introitus</li><li>Rødme og ømhed</li><li>Bredsporet gang ved svær hævelse</li><li>Feber ved absces</li></ul>'},
      {l:'Behandling', c:'<ul><li>Incision og drænage — <strong>marsupialisation</strong> foretrækkes (sy kanten op så den forbliver åben og dræner)</li><li>Antibiotika kun ved sepsis eller cellulitis</li><li>Podning ved mistanke om STD</li></ul>'},
      {l:'CAVE', c:'Hos ældre kvinder med Bartholins-kirtelforstørrelse skal der altid tages biopsi for at udelukke Bartholins-kirtelcancer.', full:true, warn:true}
    ]},
    { label:'PID', grid:[
      {l:'Definition og ætiologi', c:'Ascenderende bakterieinfektion fra vagina/cervix til uterus, tubae og adnexer. Omfatter endometritis, salpingitis, parametritis og oophoritis.<br><br><strong>Hyppigste agens:</strong> Klamydia trachomatis · gonokokker (sjælden i DK) · anaerobe bakterier.<br><strong>Disponerende:</strong> spiraloplægning (kun første måned), kontrastundersøgelse af tubae, kirurgisk abort, udskrabning.'},
      {l:'Diagnostiske kriterier — GU + mindst ét af følgende', c:'<ul><li>Bilateral ømhed og <strong>rokkeømhed</strong> ved gynækologisk undersøgelse</li><li>Temperatur &gt; 38 °C</li><li>Purulent cerviksudflåd og/eller positiv D+R (klamydia/gonore)</li><li>Forhøjede infektionsparametre (CRP, leukocytter)</li></ul>'},
      {l:'DDX', c:'<ul><li><strong>EUG</strong> — udeluk ALTID med urin-HCG</li><li>Appendicitis</li><li>Ovariecyste (rumperet/blødning/torsion)</li><li>UVI / pyelonefritis</li><li>Endometriose</li></ul>'},
      {l:'Udredning', c:'<ul><li>Urin-HCG + urinstix</li><li>CRP, leukocytter; bloddyrkning ved septisk præg</li><li>GU: rokkeømhed, udflåd</li><li>PCR podning: klamydia + gonore fra cervix og urethra</li><li>Transvaginal UL: TOA? fri væske?</li></ul>'},
      {l:'Behandling', c:'<ul><li><strong>Ambulant:</strong> tabl. tetracyklin 300 mg × 2 i 10 dage <em>eller</em> tetracyklin 100 mg × 2 + metronidazol 500 mg × 3 i 10 dage</li><li><strong>Svær/indlæggelse:</strong> IV antibiotika — overvej efter 1–2 døgn uden ambulant effekt</li><li><strong>Recidiv:</strong> laparoskopi mhp. fjernelse af adnex/salpinx</li><li>Fjernelse af spiral ved symptomer</li></ul>'},
      {l:'Sequelae — husk tallene', c:'<ul><li><strong>Infertilitet:</strong> 1 episode → 11 % · 2 episoder → 23 % · 3+ episoder → 54 %</li><li>Øget risiko for EUG (tubafaktor)</li><li>Kroniske bækkensmerter: 15–20 %</li><li>Tidlig behandling er afgørende for prognosen</li></ul>', full:true, hl:true},
      {l:'CAVE', c:'EUG skal udelukkes inden PID-diagnosen stilles. Positiv graviditetstest = EUG til det modsatte er bevist.', full:true, warn:true}
    ]},
    { label:'TOA', grid:[
      {l:'Definition', c:'Tuba-ovariel absces — en lokaliseret absces i adnexregionen som komplikation til PID eller salpingitis. <strong>59 % af kvinder med TOA er nullipara.</strong>'},
      {l:'Symptomer med frekvenser', c:'<ul><li>Abdominale smerter (uni- eller bilateralt): <strong>85 %</strong></li><li>Rokkeømhed af uterus og adnex: <strong>75 %</strong></li><li>Febrilia: <strong>65 %</strong></li><li>Gastrointestinale gener: <strong>30 %</strong></li><li>Udflåd: <strong>25 %</strong></li><li>Påvirket almentilstand + forhøjet CRP</li></ul>'},
      {l:'Mikrobiologi', c:'<ul><li>Polymikrobiel: anaerobe bakterier 50–90 %, aerobe 5–55 %</li><li>Positiv dyrkning kun ved 50–60 % — negativ dyrkning udelukker ikke TOA</li></ul>'},
      {l:'Diagnostik', c:'<ul><li>Transvaginal UL (1. valg)</li><li>MR eller CT ved tvivl eller komplicerede tilfælde</li><li>Leukocytose + markant forhøjet CRP</li></ul>'},
      {l:'Behandling', c:'<ul><li>Antibiotika (IV ved svær TOA)</li><li>UL-vejledt drænage</li><li>Kirurgi ved manglende respons eller ruptur</li></ul>'},
      {l:'CAVE', c:'Obs. fremtidig fertilitet — 59 % er nullipare ved debut. TOA kan rupturere og give peritonitis — kirurgisk akutsituation.', full:true, warn:true}
    ]}
  ]
},

{ id:'gyn_7b', spec:'GYN', num:'7b', title:'Seksuelt overførte infektioner',
  src:'Genitale infektioner K8 2025 (slides) + K8 eksamensnoter',
  sub:'<table class="nst"><thead><tr><th>Agens</th><th>Type</th><th>Nøglebehandling</th><th>Særligt</th></tr></thead><tbody><tr><td><strong>Herpes genitalis</strong></td><td>Virus (HSV1/2)</td><td>Aciclovir</td><td>Kan ikke eradikeres · obs gravid</td></tr><tr><td><strong>HPV</strong></td><td>Virus</td><td>Vaccination + screening</td><td>Type 16+18 → livmoderhalskræft</td></tr><tr><td><strong>Klamydia</strong></td><td>Bakterie</td><td>Doxycyklin 7 dage</td><td>Hyppigst · oftest asymptomatisk</td></tr><tr><td><strong>Gonore</strong></td><td>Bakterie</td><td>Ceftriaxon i.m.</td><td>Anmeldelsespligtig</td></tr><tr><td><strong>Syfilis</strong></td><td>Bakterie</td><td>Benzathin-penicillin i.m.</td><td>4 stadier · screen gravide</td></tr><tr><td><strong>Mycoplasma gen.</strong></td><td>Bakterie</td><td>Azithromycin (efter resist.)</td><td>Asympt. men alvorlig · obs neg klam/gon</td></tr></tbody></table>',
  tabs:[
    { label:'Herpes', grid:[
      {l:'Virologi og smitte', c:'Herpes simplex virus type 1 og 2. HSV2 hos ca. 20 % af befolkningen. Smitter ved hud-til-hud eller hud-til-mucosa kontakt. Kondom beskytter delvist. <strong>HSV kan ikke eradikeres</strong> — går latent i dorsale ganglier og kan reaktiveres.'},
      {l:'Symptomer', c:'<ul><li>Kløe, prikken og smerte → pustler → sår → skorpe</li><li><strong>Primær infektion:</strong> mere alvorlig — kan give almensymptomer (feber, muskelsmerter, urinproblemer). Bilaterale læsioner, cervikal involvering. Inkubation 4–14 dage, varighed 2–3 uger</li><li><strong>Recidiv</strong> (ca. 80 %): typisk unilateralt, mildere, ca. 1 uge. Udløses af stress eller menstruation</li><li>Kun 10–25 % af primærinfektioner giver klassiske symptomer</li><li>Smitter både symptomatisk og asymptomatisk</li></ul>'},
      {l:'Diagnostik og behandling', c:'<ul><li>Oftest <strong>klinisk diagnose</strong></li><li>Ved behov: prøve fra pustel/sår for HSV-typing</li><li>Aciclovir po: primær 5–10 dage · recidiv 1–5 dage</li><li>Indlæggelse ved alvorlige tilfælde</li></ul>'},
      {l:'Graviditet — vigtigt', c:'<ul><li>Undersøg for type og antistoffer</li><li>Behandles altid ved udbrud i graviditet</li><li>PO aciclovir fra GA 36 (suppressiv behandling)</li><li>IV aciclovir ved udbrud under eller tæt på fødsel</li><li>Obs neonatal herpesinfektionsrisiko</li></ul>', full:true, hl:true}
    ]},
    { label:'HPV', grid:[
      {l:'Virologi', c:'Human papillomavirus. Over 40 typer kan inficere genitalia. Smitter via hud og mucosa. Hyppigste seksuelt overførte virusinfektion.'},
      {l:'Kliniske manifestationer', c:'<ul><li><strong>Kondylomer</strong> (genitale vorter) — lavrisikotyper (6, 11)</li><li><strong>Celleforandringer → livmoderhalskræft</strong> — højrisikotyper, særligt type <strong>16 og 18</strong> (skyld i ~70 % af tilfælde)</li><li>Kan også give cancer i: mund, svælg, penis, anus, vulva, vagina</li></ul>'},
      {l:'Forebyggelse', c:'<ul><li><strong>Vaccination</strong> — tilbydes alle piger (og drenge) i vaccinationsprogrammet</li><li><strong>Screening</strong> med cervikal cytologi (smear): 23–49 år hvert 3. år · 50–64 år hvert 5. år</li><li>Muligvis udryddet om 10–15 år med fortsat vaccinations- og screeningsprogram</li></ul>'},
      {l:'Klinisk relevans', c:'HPV er årsagen til næsten al livmoderhalskræft. Vaccination + screening er de to vigtigste interventioner. Se gyn_6 (gynækologisk cancer) for cervixcancer-specifikt indhold.', full:true, hl:true}
    ]},
    { label:'Klamydia', grid:[
      {l:'Ætiologi og epidemiologi', c:'Chlamydia trachomatis — intracellulær bakterie. Hyppigste bakterielle STI i Danmark. Inkubationstid 5–21 dage.'},
      {l:'Symptomer', c:'<ul><li><strong>Oftest asymptomatisk</strong> — særligt hos kvinder</li><li>Svie ved vandladning</li><li>Uklart udflåd eller pletblødning</li></ul>'},
      {l:'Diagnostik', c:'<ul><li>PCR podning: <strong>urethra + cervix</strong> hos kvinder</li><li>Selvpodning mulig (vaginal swab)</li><li>Mænd: midtstråle urin</li></ul>'},
      {l:'Behandling', c:'<ul><li><strong>Ikke-gravid:</strong> doxycyklin 100 mg × 2 i 7 dage</li><li><strong>Gravid:</strong> azithromycin 1 g engangsdosis</li><li>Smitteopsporing obligatorisk</li></ul>'},
      {l:'Komplikationer', c:'<ul><li>Endometritis · salpingitis → tubafimbriae → EUG</li><li>Sterilitet (tubafaktor infertilitet)</li><li>Fitz-Hugh-Curtis syndrom (perihepatitis)</li><li>Gravid → neonatal konjunktivitis</li></ul>', full:true, warn:true}
    ]},
    { label:'Gonore', grid:[
      {l:'Ætiologi og epidemiologi', c:'Neisseria gonorrhoeae — gram-negativ diplokok. Sjælden i DK, hyppigst hos mænd der har sex med mænd. Smitter via sekret vaginalt, anorektalt eller oralt. <strong>Anmeldelsespligtig.</strong>'},
      {l:'Symptomer', c:'<ul><li>Ændret udflåd, mavesmerter</li><li>Pharynx og anus oftest asymptomatiske</li><li>Mange patienter asymptomatiske</li></ul>'},
      {l:'Diagnostik', c:'<ul><li>Podning til D+R fra <strong>4 steder:</strong> tonsiller, cervix, urethra og anus</li><li>Urinprøve supplerende</li></ul>'},
      {l:'Behandling og komplikationer', c:'<ul><li><strong>Behandling:</strong> ceftriaxon i.m. engangsdosis</li><li>Partnerbehandling obligatorisk</li><li><strong>Ubehandlet:</strong> endometritis, salpingitis, TOA, sepsis</li><li>Gravid → neonatal purulent konjunktivitis (ophthalmia neonatorum)</li></ul>', full:true, warn:true}
    ]},
    { label:'Syfilis', grid:[
      {l:'Ætiologi og smitte', c:'Treponema pallidum — bakterie. Smitter ved slimhindekontakt. Kan smitte fra mor til barn under graviditet/fødsel (kongenit syfilis). <strong>Gravide screenes rutinemæssigt.</strong>'},
      {l:'4 stadier', c:'<ol style="padding-left:16px;line-height:1.9"><li><strong>Primær (2–12 uger):</strong> smertefri chanker (sår) ved infektionsstedet — forsvinder spontant</li><li><strong>Sekundær (&gt;1 måned):</strong> udslæt på håndflader og fodsåler, influenzalignende symptomer</li><li><strong>Latent:</strong> asymptomatisk — tidlig (&lt;1 år) og sen latent fase</li><li><strong>Tertiær (år):</strong> CNS-skade (neurosyfilis), organskade, gummata</li></ol>'},
      {l:'Diagnostik og behandling', c:'<ul><li>Diagnostik: <strong>serologi</strong> (TPHA, VDRL)</li><li>Behandling: benzathin-penicillin G i.m.</li><li>Penicillinallergi: doxycyklin</li><li>Smitteopsporing obligatorisk</li></ul>'},
      {l:'CAVE', c:'Screen alle gravide for syfilis i 1. trimester. Kongenit syfilis kan give alvorlige fosterskader og intrauterin fosterdød.', full:true, warn:true}
    ]},
    { label:'Mycoplasma', grid:[
      {l:'Ætiologi', c:'Mycoplasma genitalium — bakterie uden cellevæg. Smitter ved slimhindekontakt. Asymptomatisk men kan give alvorlige komplikationer ved ubehandlet infektion.'},
      {l:'Symptomer', c:'<ul><li>Oftest <strong>asymptomatisk</strong></li><li>Evt. ændret udflåd, mavesmerter, dysuri</li><li>Komplikationer: endometritis, PID</li></ul>'},
      {l:'Diagnostik', c:'<ul><li>PCR: cervix-podning eller vaginal swab + midtstråle urin</li><li><strong>Obs: tænk på Mycoplasma ved symptomer med negativ klamydia og gonore</strong></li></ul>'},
      {l:'Behandling', c:'<ul><li>Behandles <strong>først efter resistensbestemmelse</strong> — stigende antibiotikaresistens</li><li>Typisk: azithromycin (efter resistenssvar)</li><li>Smitteopsporing</li></ul>'},
      {l:'CAVE', c:'Mycoplasma genitalium behandles ikke empirisk — resistensbestemmelse er obligatorisk inden behandlingsvalg. Overvejes ved vedvarende symptomer trods negativ klamydia/gonore.', full:true, warn:true}
    ]}
  ]
},
```

---

## Roadmap update

### File: `docs/roadmap.md`

In the GYN table, find:
```
| gyn_7 | Underlivsinfektion og PID | `[D]` | Converted to sub-tabs (PID / Klamydia / Gonore / Bakteriel vaginose / Candida). Awaiting medical verification. |
```

Replace with:
```
| gyn_7  | Underlivsinfektion            | `[D]` | Split from gyn_7b. Tabs: BV / Bartholinitis / PID / TOA. Slides-sourced. Awaiting verification. |
| gyn_7b | Seksuelt overførte infektioner | `[D]` | New note. Tabs: Herpes / HPV / Klamydia / Gonore / Syfilis / Mycoplasma. Slides-sourced. Awaiting verification. |
```

Append to the commit log:
```
| YYYY-MM-DD | gyn_7 + gyn_7b | Split infections note — Underlivsinfektion (4 tabs) + STD (6 tabs), slides-sourced |
```

---

## What to test in the browser

1. Notes sidebar shows both entries: "7. Underlivsinfektion" and "7b. Seksuelt overførte infektioner"
   — gyn_7b must appear immediately after gyn_7 in the list.
2. gyn_7 opens with 4 tabs: Bakt. vaginose · Bartholinitis · PID · TOA.
3. gyn_7b opens with 6 tabs: Herpes · HPV · Klamydia · Gonore · Syfilis · Mycoplasma.
4. All tab content renders — check highlight and warn cards specifically.
5. All other existing notes are unaffected.
6. If case-note linking (task 03) is already implemented, verify gyn_7 and gyn_7b
   are not broken by the id change — update caseRefs if any case referenced 'gyn_7'
   for STD content.
