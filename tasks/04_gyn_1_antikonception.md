# Task 04: Expand gyn_1 — Antikonception og abort

## Context

The current `gyn_1` note covers methods and abort basics but is missing:
- The generation comparison for p-piller (venøs vs arteriel RF → which gen to choose)
- Absolute VTE risk numbers
- The prescribing workflow (BT, anamnese, klamydiapodn. ved spiral)
- Cancer effects of p-piller
- Medicinsk vs. kirurgisk abort: fordele/ulemper with detail
- Nødprævention

This task converts `gyn_1` to a three-tab structure:
**Antikonception | Abort | Nødprævention**

**Dependency: task 02 (sub-tab UI) must be implemented before this task.**

---

## Implementation

### File: `index.html`

In `notesData`, find the entire `gyn_1` object. It starts with:

```
{ id:'gyn_1', spec:'GYN', num:1, title:'Antikonception <em>og abort</em>',
```

And ends just before:

```
{ id:'gyn_2', spec:'GYN', num:2,
```

Replace the entire `gyn_1` object (including its trailing comma) with:

```js
{ id:'gyn_1', spec:'GYN', num:1, title:'Antikonception <em>og abort</em>',
  src:'Signe noter + F24, F25, S2021',
  sub:'<table class="nst"><thead><tr><th>Metode</th><th>PI</th><th>Fordel</th><th>Kontraindikation</th></tr></thead><tbody><tr><td><strong>P-piller (kombinerede)</strong></td><td>0,3</td><td>Høj effekt, regulerer blødning, reducerer acne</td><td>Migræne med aura, VTE, hypertension, aktiv leversygdom</td></tr><tr><td><strong>Mini-piller (gestagen)</strong></td><td>0,3</td><td>Ingen arteriel tromboserisiko, kan bruges ved amning</td><td>Aktiv/tidl. VTE, svær leversygdom, gestagenafhængig tumor</td></tr><tr><td><strong>Hormonspiral</strong></td><td>0,1</td><td>Høj compliance, reducerer blødning markant</td><td>Submukøse fibromer, gentagne PID, gestagenafhængig tumor</td></tr><tr><td><strong>Kobberspiral</strong></td><td>0,6</td><td>Ingen hormoner, høj compliance, kan bruges som nødprævention</td><td>Submukøse fibromer, gentagne PID</td></tr><tr><td><strong>P-stav</strong></td><td>0,05</td><td>3 år, ingen VTE-risiko, compliance</td><td>Gestagenafhængig tumor, svær leversygdom</td></tr><tr><td><strong>Kondom</strong></td><td>2–15</td><td>Eneste metode der beskytter mod kønssygdomme</td><td>Ingen</td></tr></tbody></table>',
  tabs:[
    { label:'Antikonception', grid:[
      {l:'Anamnese inden ordinering', c:'<ul><li>Migræne med aura (kontraindikation til kombinerede p-piller)</li><li>Tidligere VTE / DVT / LE — familiær disposition, koagulopati (Faktor V Leiden, protein C/S-mangel)</li><li>Alder &gt;35 år, rygning, BMI</li><li>BT — hypertension</li><li>Medicin: epilepsimedicin reducerer p-pillernes effekt!</li><li>Aktuel/tidl. brystkræft, leverlidelse</li><li>Compliance — hvad kan patienten være med til?</li></ul>'},
      {l:'Undersøgelse og opfølgning', c:'<ul><li>Mål BT <strong>nu og efter 3 måneder</strong></li><li>Journalfør information om tromboserisiko</li><li>Klamydiapodning inden spiraloplægning</li><li>GU ved spiraloplægning</li></ul>'},
      {l:'Valg af p-pille — generationsguide', c:'<p><strong>Standardvalg:</strong> 2. generations kombinationspræparat (kvinder &lt;30 år uden disposition)</p><p style="margin-top:8px"><strong>RF for venøs tromboemboli</strong> (overvægt, åreknuder, familiær VTE-disposition):<br>→ 2. generationspræparat eller ren gestagenkontraception</p><p style="margin-top:8px"><strong>RF for arteriel tromboemboli</strong> (rygning, let forhøjet BT, migræne, familiær disposition):<br>→ 3. generationspræparat eller ren gestagenkontraception</p><p style="margin-top:8px"><strong>Svær at huske daglig pille:</strong> p-ring eller p-plaster (ugentlig/månedlig) — samme effektivitet</p>', full:true},
      {l:'VTE-risiko — absolutte tal', c:'<ul><li>Unge kvinder uden p-piller: <strong>1 / 10.000 / år</strong></li><li>2. gen p-piller: 3× øget risiko</li><li>3. gen p-piller: 4–6× øget risiko</li><li>Graviditet: 8–10× øget risiko</li><li>NNT: 2000 kvinder skal skifte fra 3. til 2. gen for at forebygge 1 VTE/år</li></ul>', hl:true},
      {l:'P-piller og cancer', c:'<ul><li>Samlet cancerrisiko: neutral til let nedsat (−12 %)</li><li>Beskyttende: ovariecancer ↓ 50 %, endometriecancer ↓, kolorektal cancer ↓</li><li>Øget: mammacancer ↑ (RR 1,2) — forsvinder 10 år efter seponering</li><li>BRCA-mutation: ingen signifikant øget risiko ved brug &lt;5 år</li></ul>'},
      {l:'Eksamen-fælder', c:'<ul><li>P-piller ordineret uden at spørge til kontraindikationer = dumpegrund (F25)</li><li>Epilepsimedicin reducerer effekten — brug anden metode eller højere dosis</li><li>Klamydiapodning glemt inden spiraloplægning = trækker ned</li><li>BT skal måles nu og efter 3 måneder — glem ikke opfølgning</li></ul>', full:true, warn:true}
    ]},
    { label:'Abort', grid:[
      {l:'Lovpligtige punkter', c:'<ul><li><strong>Blanket A</strong> — kvinden skriver under på informeret samtykke. Obligatorisk inden indgreb. Sendes med henvisning.</li><li><strong>Blanket B</strong> — ved pt. &lt;18 år eller umyndiggjort (forældre/værge underskriver)</li><li>Rådgivning tilbydes altid — støttesamtale før og efter indgreb</li><li>GU + klamydiapodning</li><li>Plan for fremtidig prævention</li><li>Fri abort til GA 12+0. Efter 12+0 til uge 22 → abortsamråd</li><li>Mindreårig (&lt;15 år): skærpet indberetningspligt → kontakt forældre og sociale myndigheder</li></ul>', full:true},
      {l:'Undersøgelser', c:'<ul><li>Urin-HCG (bekræft graviditet)</li><li>Transvaginal UL: intrauterin graviditet? CRL-mål → GA</li><li>GU: uterus størrelse, Hegars tegn, cyanotisk portio</li><li>Klamydiapodning fra cervix og uretra</li><li>Blodtype + BAC-test (Anti-D til Rh-negative ved GA ≥ 8+0)</li></ul>'},
      {l:'Medicinsk abort (&lt;9 uger, evt. op til 12)', c:'<ol style="padding-left:16px;line-height:1.9"><li>Mifegyn (mifepriston) po — antiprogesteron → øger uterins følsomhed for prostaglandin</li><li>48 timer efter → Cytotec (misoprostol) vaginalt — prostaglandinanalog → uteruskontraktioner</li></ol><p style="margin-top:8px"><strong>Fordele:</strong> Ingen bedøvelse, lav infektionsrisiko (1–2%), ambulant, ingen perforationsrisiko</p><p style="margin-top:6px"><strong>Ulemper:</strong> Tager længere tid, inkomplet abort (5%), kraftig blødning (10–14 dage), bivirkninger (kvalme, opkast)</p>'},
      {l:'Kirurgisk abort (&gt;6 uger, anbefales &gt;9 uger)', c:'<p>Vakuumaspiration i generel anæstesi. Grænse: &lt;13 uger.</p><p style="margin-top:8px"><strong>Fordele:</strong> Hurtigt overstået, færre smerter, mindre blødning, lavere risiko for inkomplet abort</p><p style="margin-top:6px"><strong>Ulemper:</strong> Kræver bedøvelse, risiko for uterusperforering (&lt;0,5 %), infektion (3–5 %)</p>'},
      {l:'Anbefaling og opfølgning', c:'<ul><li>1. trimester: medicinsk foretrukket (lavest komplikationsrisiko)</li><li>Serum-HCG: måles inden og 14 dage efter indgrebet (bekræft komplet abort)</li><li>Fremtidig prævention planlægges ved samme konsultation</li></ul>'},
      {l:'Eksamen-fælder', c:'<ul><li>Blanket A glemt = grænsetilfælde. Blanket A glemt + manglende information om metoder = dumpegrund</li><li>Anti-D til Rh-negative ved GA ≥ 8+0 — hyppigt overset</li><li>Klamydiapodning obligatorisk inden kirurgisk abort</li></ul>', full:true, warn:true}
    ]},
    { label:'Nødprævention', grid:[
      {l:'Indikationer', c:'<ul><li>Ubeskyttet samleje</li><li>Glemt p-pille uge 1 eller 2 (&gt;12 timer forsinket)</li><li>Kondomsvigt</li></ul>'},
      {l:'Præparater og tidsvindue', c:'<table class="nst"><thead><tr><th>Præparat</th><th>Tidsvindue</th><th>Effektivitet</th><th>Recept</th></tr></thead><tbody><tr><td><strong>Norlevo</strong> (levonorgestrel 1,5 mg)</td><td>&lt;72 timer</td><td>~85 %</td><td>Ikke receptpligtig</td></tr><tr><td><strong>EllaOne</strong> (ulipristalacetat)</td><td>&lt;120 timer (5 dage)</td><td>~90 %</td><td>Receptpligtig</td></tr><tr><td><strong>Kobberspiral</strong></td><td>&lt;5 dage</td><td>&gt;99 %</td><td>Kræver GU</td></tr></tbody></table>'},
      {l:'Praktisk håndtering', c:'<ul><li>Jo hurtigere nødprævention tages, desto bedre effekt</li><li>Bivirkninger Norlevo: kvalme 10–15 %, opkast 6 % — gentag dosis hvis opkast inden 3 timer</li><li>Husk graviditetstest efter 5–6 uger</li><li>Informer om kønssygdomsrisiko — tilbyd klamydiatest</li><li>Planlæg fremtidig prævention</li></ul>'},
      {l:'Glemt p-pille', c:'<ul><li><strong>Uge 1 eller 2:</strong> Tag den glemte pille straks + nødprævention ved samleje de seneste 5 dage</li><li><strong>Uge 3:</strong> Færdiggør blisterpakken — spring den p-pille-frie periode over og start ny pakke direkte</li></ul><p style="margin-top:8px">Obs: Størst risiko for utilsigtet ovulation ved glemte piller i <strong>starten af pakken</strong> (FSH stiger igen og follikel kan modnes)</p>'},
      {l:'CAVE', c:'Kobberspiral er mest effektiv og foretrukkes, hvis patienten accepterer den, og der ikke er kontraindikationer. Overvej samtidig klamydiatest.', full:true, warn:true}
    ]}
  ]
},
```

---

## Roadmap update

### File: `docs/roadmap.md`

Find:
```
| gyn_1 | Antikonception og abort | `[✓]` | Prescribing workflow + generation comparison thin — minor revision planned |
```

Replace with:
```
| gyn_1 | Antikonception og abort | `[D]` | Expanded to 3 tabs: Antikonception / Abort / Nødprævention. Awaiting medical verification. |
```

Append to the commit log:
```
| YYYY-MM-DD | gyn_1 | Expand antikonception note — generation guide, VTE tal, abort fordele/ulemper, nødprævention |
```

---

## What to test in the browser

1. Open gyn_1 — three tabs should appear: Antikonception, Abort, Nødprævention.
2. Antikonception tab: verify generation-guide card, VTE-risiko tal, eksamen-fælder.
3. Abort tab: verify both lovpligtige punkter and medicinsk vs. kirurgisk with fordele/ulemper.
4. Nødprævention tab: verify præparatoversigt table renders correctly.
5. Switch to another note and back — tabs reset to Antikonception.
6. All other notes must be unaffected (flat grid still renders).
