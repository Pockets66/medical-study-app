# Medical Study App

A standalone HTML tool for studying in med school

## Current state
This project is based on an existing standalone HTML tool:
- `reference/K8_Studieguide.html`

Reference files are READ-ONLY. Do not modify them. The merged app lives in
`index.html` at the project root (create it when needed).

## Architecture constraints
- Single HTML file. All CSS inline in `<style>`, all JS inline in `<script>`.
- Vanilla JS only. No frameworks, no build step, no npm, no bundler.
- Must work when opened directly via `file://` in a browser. No server required.
- Persistence is `localStorage` under a single key: `wm_unified_v1`.

## Data model
The data model lives in `docs/data-model.md`. Read it before making changes that touch state shape. If a change requires altering the schema, update that doc
in the same commit.

## Roadmap
The content roadmap lives in `docs/roadmap.md`. It tracks the status of every note card (planned / in progress / drafted / verified / committed).

- When starting work on a note, move its status to `[~]`.
- When a note is written into `index.html`, move its status to `[D]` and add a row to the commit log at the bottom of the file.
- Never mark a note `[✓]` — that is done by the owner after medical review.
- If new topics are identified during work, add them to the Backlog section.

## Style
- Match existing CSS variables in reference files
- Keep inline `<style>` and `<script>` — no external files

## Constraints
- Don't break existing localStorage data if possible (migration path)
- Keep it under ~3000 lines; if bigger, we split into modules later

## Tasks
Discrete content tasks live in `tasks/*.md`. When a task file is present:
1. Read the task file fully before touching any other file.
2. Implement exactly what the task specifies — no scope creep.
3. Update `docs/roadmap.md` as instructed in the task file.
4. Delete the task file after successful implementation.
5. Summarize what changed and what to test in the browser.

## Workflow
- Work in small slices. One feature, one commit.
- Before large changes, propose a plan in chat and wait for confirmation.
- After edits, summarize what changed and what to test in the browser.
- Never delete or rewrite large sections without explaining why first.