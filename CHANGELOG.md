# Changelog

## v1.2.0 - 2026-10-02

- Updated the displayed NetDraw version to `v1.2.0`.
- Added a new **Note** object type (Annotations palette section) for free-form text and annotations: a title chip, wrapped body text, rounded solid-bordered box, and automatic growth to fit the content.
- Notes are edited from the properties panel (Title and Text), support the same filter/layer tagging, accent color, ordering, resizing, copy/paste, and connections as other objects, and participate in object search via their body text.
- Existing saved diagrams load unchanged; the new `text` field is optional and validated on import.

## v1.1.13 - 2026-10-02

- Updated the displayed NetDraw version to `v1.1.13`.
- Added a **Marquee** box-select tool (`B`): drag a box anywhere on the canvas to select the nodes and zones it touches. Plain drag replaces the selection, `Shift`+drag adds to it, and `Ctrl`/`Cmd`+drag toggles individual objects. The tool stays active for consecutive boxes, and middle/right/`Space`+drag still pans.

## v1.1.12 - 2026-10-02

- Updated the displayed NetDraw version to `v1.1.12`.
- Added object search: open the **Search objects** box in the topbar to search the current page by object label, device name, IP address, or DNS name. Results list each object with the matching field, and selecting one selects it and centers the canvas on it.

## v1.1.11 - 2026-10-02

- Updated the displayed NetDraw version to `v1.1.11`.
- Added filters/layers: create document-wide named, colored filters in an Edit filters dialog, then tag any node, connection, zone, or swimlane from its properties panel (single or multi-selection).
- Added a floating **Filter views** checklist at the top-left of the canvas for enabling and disabling filters; it can be collapsed and remembers its state.
- Toggling one or more filters dims every object that does not match, while keeping the matching object's containing zones and swimlanes (parents, grandparents, …) lit. Connections stay visible when tagged or when both endpoints match.
- SVG/PNG/GIF exports prompt to render the full diagram or exactly what is on screen while filters are active.

## v1.1.10 - 2026-10-02

- Updated the displayed NetDraw version to `v1.1.10`.
- Added multi-object properties editing: select two or more nodes, connections, zones, or swimlanes to edit labels, shared fields, disposition, effects, colors, and connection settings together, with mixed-value indicators.
- Added automatic label wrapping with manual line breaks; the in-canvas label editor is now a multiline textarea (Enter commits, Shift+Enter adds a line).
- Object, connection, zone, and swimlane sizing now measures wrapped text so cards, label tags, and swimlane title bands grow to fit.
- Dragging a zone now also moves any zones nested inside it, recursively, along with their member objects.
- The properties panel now scrolls when its content overflows the viewport.

## v1.1.9 - 2026-08-16

- Updated the displayed NetDraw version to `v1.1.9`.
- Hardened JSON import validation so connection IDs cannot collide with node or zone IDs.
- Cleaned up video and audio capture resources when recording cannot start.
- Changed the upper-right trash button to warn before resetting the full document to a new blank page.
- Clarified README wording for the in-page copy/paste clipboard and browser-supported recording formats.

## v1.1.8 - 2026-08-10

- Updated the displayed NetDraw version to `v1.1.8`.
- Added in-page copy and paste for selected nodes, zones, and swimlanes.
- Pasted groups preserve connections whose source and destination are both included in the copied selection.

## v1.1.7 - 2026-08-06

- Updated the displayed NetDraw version to `v1.1.7`.
- Added object resize handles for selected nodes, with saved custom dimensions and backward-compatible automatic sizing for existing diagrams.
- Added connections between zones and objects, including zone-to-zone and zone-to-node links using the existing side-point routing model.
- Added `Down`, `Missing`, and `Unavailable` effects/status entries for nodes.
- Added NetDraw version metadata to PNG and animated GIF exports.
- Fixed zone connection hit testing so the temporary connection preview does not block zone targets.

## v1.1.6 - 2026-08-05

- Updated the displayed NetDraw version to `v1.1.6`.
- Added a top palette control to collapse or expand all object sections at once.

## v1.1.5 - 2026-08-05

- Updated the displayed NetDraw version to `v1.1.5`.
- Added an A-AUTO palette section under HULFT with product-fit icons for cross-platform job scheduling, batch jobs, progress monitoring, A-AUTO/LINK, ERP jobs, carryover jobs, and 24/365 operation.

## v1.1.4 - 2026-08-05

- Updated the displayed NetDraw version to `v1.1.4`.
- Added a HULFT palette section under Azure with product-fit icons for HULFT10 file transfer, management information, jobs, triggers, code conversion, ciphering, cloud storage, logs, and clustering.

## v1.1.3 - 2026-08-05

- Updated the displayed NetDraw version to `v1.1.3`.
- Added an Azure palette section under Google Cloud Platform with 624 entries from the official Microsoft Azure Architecture Icons SVG package.

## v1.1.2 - 2026-08-05

- Updated the displayed NetDraw version to `v1.1.2`.
- Added a Google Cloud Platform palette section under AWS with 250 entries from the official Google Cloud icon packages.

## v1.1.1 - 2026-08-05

- Updated the displayed NetDraw version to `v1.1.1`.
- Added an AWS palette section under Docker with 305 AWS service entries from the official AWS Architecture Icons package.

## v1.1.0 - 2026-08-05

- Updated the displayed NetDraw version to `v1.1.0`.
- Added page-level Journey workflows with step authoring, object picking, captions, camera focus, and playback controls.

## v1.0.0 - 2026-08-05

- Started versioning at `v1.0.0` and displayed the version next to the NetDraw name in the top-left header.
- Added connection endpoint points so lines can attach to the top, right, bottom, or left side of each object.
- Added connection arrow options for start, end, and two-way directions.
- Changed animated traffic flow so start and end arrow connections flow toward the arrow.
- Added connection route choices: curved, straight, and elbow.
- Added draggable bend handles for selected elbow connections.
- Added object ordering controls for selected nodes, zones, swimlanes, and connections.
- Fixed the connection properties panel delete button.

## 2026-07-08

- Added bottom page tabs for multi-page diagrams, including add, rename, switch, and delete page actions.
- Changed JSON save/load to use one portable document file containing all pages, while keeping old single-page JSON imports compatible.
- Added Docker palette section with Docker, Container, Image, Volume, Network, and Port items.
- Added light/dark mode toggle in the top toolbar.
- Made SVG-rendered nodes, labels, edge chips, zones, handles, and hint/editor overlays theme-aware.
- Added browser-local diagram restore on startup, with clear-canvas fallback when no valid save exists.
- Changed empty-canvas dragging to pan by default; `Shift`+drag keeps marquee selection.
- Made left sidebar palette sections collapsible and persisted their collapsed state locally.
- Moved Load Balancer into the Network palette section.
- Added server palette items: Mainframe, Solaris, Server Appliance, and ESX.
- Added People & Misc palette items: SMS and Call; moved Fax into People & Misc.
- Hardened JSON import and local restore with document normalization and validation.
- Fixed duplicated swimlanes sharing lane arrays with the original.
- Fixed GIF export selection restoration after export failures.
- Added README and changelog documentation.
