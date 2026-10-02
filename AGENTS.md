# AGENTS.md

## Project
NetDraw is a self-contained browser network-diagram editor. The entire app — HTML, CSS,
JS, and all embedded icon data — lives in `NetDraw.html` (~11k lines, ~3.2 MB). There is
no build step, package manager, test suite, lint, or CI. Run it by opening
`NetDraw.html` directly in a modern browser (`xdg-open NetDraw.html`).

## File map (NetDraw.html)
- ~1–495: markup + CSS (theme variables at top; `body.light` overrides).
- ~496–8476: constants/data. `ICONS` (~528), `EFFECTS` (~658), `FIELD_DEFS` (~698),
  `TYPES` (~745), then the huge `AWS_SERVICE_ITEMS` (~878), `GCP_SERVICE_ITEMS` (~1188),
  `AZURE_SERVICE_ITEMS` (~3443) icon arrays that make up most of the file, and
  `PALETTE_GROUPS` (~8440).
- ~8477–11182: logic — state/history/persistence, rendering, interaction, properties
  panel, export (PNG/SVG/GIF/video), and `boot()` at the end.
- Do not read the whole file or grep broad terms; the embedded SVG strings flood results.
  Use targeted line ranges and anchored keywords.

## State model
- A document is `{version: DOC_VERSION(2), activePageId, pages:[{id,name,state,view}]}`,
  where `state = {nodes, edges, zones, journey:{steps:[]}}` and `view = {x,y,k}`.
- `state` / `view` are live references to the active page. `persistCurrentPage()` copies
  them back before serialization; `setActivePage()` reassigns them. Persist before
  switching or adding pages.
- localStorage keys: `netdraw.doc.v1` (autosaved document), `netdraw.theme.v1`,
  `netdraw.palette.v1`.
- All file import / local restore goes through `normalizeState` / `normalizeFileDoc`.
  Keep changes backward compatible and preserve ID-collision validation across nodes,
  zones, and edges.

## Mutation convention
- Mutate `state`, then call `commit()` (pushes undo snapshot, resets redo, schedules
  `saveSoon()`), then `renderAll()`, and usually update `selection`.
- Never write the document to localStorage directly; use `saveSoon()`.

## Adding an object type
Needs coordinated edits or it fails silently: `ICONS` (SVG), `TYPES` (name/accent/fields),
`PALETTE_GROUPS` (placement). Cloud items also require an entry in the relevant
`*_SERVICE_ITEMS` array. User text is escaped with `esc()`; icons are injected as raw SVG —
keep that boundary.

## Releases & versioning
The version is duplicated and must be updated together:
- `NetDraw.html` logo `<span class="sub">vX.Y.Z</span>` (~line 330). Runtime `appVersion()`
  reads it from the DOM and stamps it into PNG `tEXt` and GIF XMP export metadata.
- `README.md` line 3.
- A new `## vX.Y.Z - YYYY-MM-DD` heading in `CHANGELOG.md`.
Commit style: imperative subject (e.g. "Add zone connections"); releases are committed as
`Release NetDraw vX.Y.Z`. Work directly on `main`.

## Verifying changes
No automated tests. Verify manually in a browser: load `NetDraw.html`, watch the console
for errors, and exercise save/load (JSON round-trip), undo/redo, and export.
