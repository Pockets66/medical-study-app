# Data Model

All data is declared as inline JS arrays in `index.html`. There is no backend.
Persistence (user progress) is stored in `localStorage` under the key `wm_unified_v1`.

---

## casesData — OSCE cases

```js
{
  id:    'gyn_1',          // string, unique — spec prefix + number
  spec:  'GYN',            // 'GYN' | 'OBS'
  num:   1,                // display number (integer)
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

---

## notesData — reference notes

```js
{
  id:   'gyn_1',           // string, unique — matches casesData convention
  spec: 'GYN',             // 'GYN' | 'OBS'
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
  ]
}
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
