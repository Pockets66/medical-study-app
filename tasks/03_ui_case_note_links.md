# Task 03: UI — Bidirectional case ↔ note linking

## Context

Cases and notes share a consistent ID convention but are currently siloed.
This task adds:
- A "Relaterede noter" link bar at the bottom of each case view
- A "Relaterede cases" link bar at the bottom of each note view

Both navigate directly to the linked item: clicking a note link switches to the
Notes tab and opens that note; clicking a case link switches to the Cases tab
and opens that case.

No emojis. Plain text labels and minimal styling only.

---

## Implementation

### 1. Data — add `noteRef` to casesData

For each case object that has a matching note, add a `noteRef` array.
Example:

```js
{ id:'case_pid', ..., noteRef:['gyn_7'] }
```

Add `noteRef` to the following cases (match by topic):

| Case id | noteRef |
|---------|---------|
| `case_pid` (underlivsinfektion) | `['gyn_7']` |
| `case_praeeklampsi` | `['obs_1']` |
| `case_gdm` | `['obs_6']` |
| `case_praeterm` | `['obs_7']` |
| `case_vaekst` | `['obs_5']` |

Look up the actual case `id` values in `casesData` — use the IDs as they appear
in the data, not the display titles.

---

### 2. Data — add `caseRefs` to notesData

For each note that has a matching case, add a `caseRefs` array.
Example:

```js
{ id:'gyn_7', ..., caseRefs:['case_pid'] }
```

Add `caseRefs` to the same pairs listed above (mirror of the table).

---

### 3. CSS — add link bar styles

Find the comment:
```css
/* NOTE SUB-TABS */
```

Insert immediately before it:

```css
/* CROSS-LINKS */
.xlink-bar { display:flex; flex-wrap:wrap; gap:8px; margin-top:24px; padding-top:20px; border-top:1px solid var(--border); align-items:center; }
.xlink-label { font-size:11px; letter-spacing:.08em; text-transform:uppercase; color:var(--text-3); margin-right:4px; }
.xlink-btn { padding:6px 12px; border-radius:6px; border:1px solid var(--border-strong); background:var(--surface); color:var(--text-2); font-size:13px; cursor:pointer; transition:all .15s; }
.xlink-btn:hover { background:var(--surface2); color:var(--text); }
```

---

### 4. JS — add navigation helpers

Find `function switchNoteTab(`. Immediately before it, add:

```js
function goToNote(noteId) {
  // Switch to notes pane
  document.querySelectorAll('.tab-btn').forEach(function(b){ b.classList.remove('active'); });
  document.querySelectorAll('.pane').forEach(function(p){ p.classList.remove('active'); });
  var notesBtn = document.querySelector('.tab-btn[data-pane="notes"]');
  var notesPane = document.getElementById('pane-notes');
  if (notesBtn) notesBtn.classList.add('active');
  if (notesPane) notesPane.classList.add('active');
  showNote(noteId);
  // Scroll sidebar item into view
  var item = document.getElementById('ni_' + noteId);
  if (item) item.scrollIntoView({ block:'nearest' });
}

function goToCase(caseId) {
  // Switch to cases pane
  document.querySelectorAll('.tab-btn').forEach(function(b){ b.classList.remove('active'); });
  document.querySelectorAll('.pane').forEach(function(p){ p.classList.remove('active'); });
  var casesBtn = document.querySelector('.tab-btn[data-pane="cases"]');
  var casesPane = document.getElementById('pane-cases');
  if (casesBtn) casesBtn.classList.add('active');
  if (casesPane) casesPane.classList.add('active');
  openCase(caseId);
}
```

---

### 5. JS — render link bar in `showNote()`

At the very end of `showNote()`, just before:
```js
  document.getElementById('notesMain').innerHTML = html;
```

Add:

```js
  if (n.caseRefs && n.caseRefs.length) {
    html += '<div class="xlink-bar">';
    html += '<span class="xlink-label">Relaterede cases</span>';
    n.caseRefs.forEach(function(cid) {
      var c = casesData.find(function(x){ return x.id === cid; });
      if (!c) return;
      html += '<button class="xlink-btn" onclick="goToCase(\'' + cid + '\')">'
            + c.title + '</button>';
    });
    html += '</div>';
  }
```

---

### 6. JS — render link bar in the case view

Find the function that renders the case step view (look for where
`case-header` HTML is assembled or where steps are rendered into the DOM).

In that render function, after the steps are rendered and before the
`case-nav` buttons div, add:

```js
  if (c.noteRef && c.noteRef.length) {
    html += '<div class="xlink-bar">';
    html += '<span class="xlink-label">Relaterede noter</span>';
    c.noteRef.forEach(function(nid) {
      var n = notesData.find(function(x){ return x.id === nid; });
      if (!n) return;
      var title = n.title.replace(/<[^>]+>/g, '');
      html += '<button class="xlink-btn" onclick="goToNote(\'' + nid + '\')">'
            + title + '</button>';
    });
    html += '</div>';
  }
```

---

### 7. HTML — verify tab buttons have `data-pane` attributes

The `goToNote()` and `goToCase()` helpers use
`querySelector('.tab-btn[data-pane="notes"]')`. Check that the main nav tab
buttons have matching `data-pane` attributes, e.g.:

```html
<button class="tab-btn" data-pane="cases" ...>Cases</button>
<button class="tab-btn" data-pane="notes" ...>Notater</button>
```

If they use a different attribute or selector, update the helper functions to
match whatever selector pattern is already used in the existing tab-switching
logic. Do not change the existing tab-switching logic itself.

---

### 8. Update `docs/data-model.md`

In `## casesData`, add after the `steps` field:

```md
- **`noteRef`** *(optional string[])* — IDs of related notes in `notesData`.
  Rendered as a link bar at the bottom of the case view.
```

In `## notesData`, add after the `grid` / `tabs` fields:

```md
- **`caseRefs`** *(optional string[])* — IDs of related cases in `casesData`.
  Rendered as a link bar at the bottom of the note view.
```

---

### 9. Update `docs/roadmap.md`

Append to the commit log:
```
| YYYY-MM-DD | ui | Add bidirectional case-note linking — noteRef + caseRefs |
```

---

## What to test in the browser

1. Open a case that has a `noteRef` — a "Relaterede noter" bar should appear
   below the steps with a button for each linked note.
2. Click the button — the Notes tab activates and the correct note opens.
3. Confirm the sidebar highlights the correct note item.
4. Open a note that has `caseRefs` — a "Relaterede cases" bar appears at the
   bottom.
5. Click it — the Cases tab activates and the correct case opens.
6. Open a note without `caseRefs` — no link bar visible.
7. Open a case without `noteRef` — no link bar visible.
