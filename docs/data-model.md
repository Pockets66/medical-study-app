# Data Model

All data is declared as inline JS arrays in `index.html`. There is no backend.
Persistence (user progress) is stored in `localStorage` under the key `wm_unified_v1`.

---

## casesData — OSCE cases

```js
{
  id:    'gyn_1',          // string, unique — spec prefix + number
  spec:  'GYN',            // 'GYN' | 'OBS' | 'PEDS'
  num:   1,                // display label — string or integer (e.g. 7, '7b')
  title: 'Underlivsinfek…',// plain text (shown on card + case header)
  src:   'F24, E23',       // exam sources, plain text
  sub:   '<p>…</p>',       // optional HTML snippet shown below title (definitions / subtypes table)
  steps: [                 // ordered array of reveal-steps
    {
      q:  'Hvilke symptomer…',  // question text (plain)
      a:  '<ul><li>…</li></ul>',// answer HTML
      hl: 'Husk: …',           // optional — rendered as purple highlight box
      warn: 'Cave: …'          // optional — rendered as amber warning box
    }
  ]
}
```

**CSS colour mapping for `spec`:**
| spec | CSS var |
|------|---------|
| GYN  | `--gyn` / `--gyn-bg` |
| OBS  | `--obs` / `--obs-bg` |
| PEDS | `--paed` / `--paed-bg` |

---

## notesData — reference notes

```js
{
  id:   'gyn_1',           // string, unique — matches casesData convention
  spec: 'GYN',             // 'GYN' | 'OBS' | 'PEDS'
  num:  1,                 // sidebar display number
  title:'Underlivsinfektion <em>og PID</em>', // may contain <em>
  src:  'F24 (stand), E23',// exam sources
  sub:  '<table…</table>', // optional HTML — shown in "Definitioner / subtyper" block
  grid: [                  // array of content cards rendered in a 2-col CSS grid
    {
      l:    'PID — diagnostik',  // card label (plain text)
      c:    '<ul>…</ul>',        // card body HTML
      full: true,                // optional — spans both columns
      hl:   true,                // optional — coloured highlight background
      obs:  true,                // optional — use OBS colour instead of GYN for hl
      warn: true                 // optional — amber warning style (overrides hl)
    }
  ],
  tabs: [                  // optional — if present, replaces grid[]. Renders a tab bar.
    {
      label: 'PID',        // tab button text
      grid:  [ ... ]       // same grid-item structure as flat grid[]
    }
  ],
  caseRefs: ['underlivsinf'] // optional string[] — IDs of related cases (openCase keys).
                             // Rendered as a link bar at the bottom of the note view.
}
```

Case HTML elements carry the complementary link bar as injected static HTML before
`<div class="case-nav">`. The case id used in `openCase('id')` is the bare key
(e.g. `praeeklampsi`, `underlivsinf`) — not prefixed with `case-`.
```

---

## localStorage schema — `wm_unified_v1`

Stored as JSON. Top-level keys:

```js
{
  "caseProgress": {
    // keyed by case id
    "gyn_1": {
      "revealedSteps": [0, 1, 2],  // indices of steps the user has revealed
      "completed": true             // true when all steps revealed
    }
  }
}
```

**Migration rule:** Always read with a fallback (`|| {}`). When adding new keys,
write them alongside existing ones — never replace the whole object.

---

## CSS variables (colour palette)

Defined in `:root` in `index.html`. Do not hardcode hex values in new code.

```
--bg           page background
--surface      card / panel background
--surface2     hover / subtle background
--border       default border
--border-strong stronger border (hover states)
--text         primary text
--text-2       secondary text
--text-3       muted / meta text
--obs          OBS accent (blue)
--obs-bg       OBS tint background
--gyn          GYN accent (purple)
--gyn-bg       GYN tint background
--paed         PAED accent (green)
--paed-bg      PAED tint
--neo          NEO accent (amber)
--neo-bg       NEO tint
--accent       global accent (red-orange)
--radius       default border-radius (10px)
```

## flowData — Symptomudredning (diagnostiske flowcharts)

```js
{
  id:    'akut_underlivssmerter', // string, unique
  spec:  'GYN',                   // 'GYN' | 'OBS' | 'PEDS' — drives card badge
  title: 'Akutte smerter...',     // shown on picker card + trail
  src:   'Eksamenssæt + noter',   // provenance, plain text
  start: 'start',                 // id of the entry node
  nodes: {                        // map of nodeId -> node
    // QUESTION node (has opts[]):
    start: {
      q:       '...',             // question text (plain)
      why:     '...',             // optional reasoning (HTML)
      redflag: '...',             // optional red-flag callout (HTML)
      ask:     [ '...' ],         // optional checklist (HTML strings)
      opts:    [ { lead:'...', hint:'...', next:'nodeId' } ]
    },
    // TERMINAL node (no opts[]):
    eug: {
      dx:'...', dxsub:'...',      // diagnosis name + subtitle
      urgency:'akut',             // 'akut' | 'haster' | 'rolig' (badge)
      findings:   [ '...' ],      // HTML strings
      ddx:        [ { d:'...', r:'...' } ], // dx + reason
      behandling: [ '...' ],
      ki:         [ '...' ],      // kontraindikationer & cave
      prognose:   '...',
      caseRef:    'tidliggrav'    // goToCase() key, or null
    }
  }
}
```

Renderer reads `flowData`; node is terminal iff it has no `opts`. `caseRef`
links out via the existing `goToCase()`.
