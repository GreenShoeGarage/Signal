# TACKBOARD v1.1.3

**TACKBOARD — A Simple Visual Thinking Space**

TACKBOARD is a calm, local-first virtual whiteboard for arranging freeform sticky notes, structured Kanban notes, stickers, text labels, frames, connectors, and freehand annotations.

## What changed in v1.1.3

TACKBOARD now has two distinct mouse interaction tools at the top of the left toolbar:

- **Select — arrow icon (`V`)**: click objects to select them, left-drag empty board space to draw a multi-selection rectangle, and drag selected objects to move them.
- **Pan — hand icon (`H`)**: left-click and drag anywhere on the board—including directly over notes, stickers, drawings, or connectors—to move the complete board view.

The two modes no longer compete for the same ordinary left-drag gesture. The active tool is visibly highlighted and exposed to assistive technology through its pressed state.

Additional behavior:

- `Space + drag` and middle-button drag still provide temporary panning from any tool.
- The Select tool retains additive marquee selection with `Shift`, `Ctrl`, or `Cmd`.
- Double-click creation and object editing are intentionally inactive while the Pan tool is selected, preventing accidental edits while navigating.
- One-finger dragging with the Pan tool pans from any starting point on touch devices; two-finger pinch/pan remains available.
- The visible version and offline cache were updated to v1.1.3.

## Included from earlier releases

- Sticker library with thumbs up/down, green check, **Red X**, red exclamation, yellow question, blue box, arrows, star, heart, idea, flag, plus, and minus.
- Sticker placement, drag-and-drop, movement, resizing, replacement, grouping, layering, connectors, search, persistence, and export.
- Higher-contrast text across light-colored sticky notes and structured Kanban notes.
- Structured Kanban notes with expanded and compact views.
- Local autosave, multiple boards, undo/redo, search, filters, JSON import/export, PNG export, and PDF/print output.

## Run it

TACKBOARD has no backend and no build step.

### Simple local use

Open `index.html` in a modern browser. Core board features and local persistence work directly from the file.

### Recommended hosted or local-server use

Serve the folder from any normal static web host. This also enables the included service worker for offline reopening after the first visit.

For a local server:

```bash
python3 -m http.server 8080
```

Then open `http://localhost:8080`.

## Core workflow

**CREATE → ARRANGE → CONNECT → REFINE → SAVE**

- Choose the **Select arrow** when selecting, marquee-selecting, moving, or resizing board objects.
- Choose the **Pan hand** when left-dragging the board view.
- Double-click empty board space in Select mode to create a blank sticky note.
- Use the Sticky Note tool or `Shift + N` to choose Blank Note or Kanban.
- Use the Sticker tool or `Shift + S` to open the sticker picker. Plain `S` activates the most recently used sticker.
- Drag a note by its header; stickers and text labels can be dragged from anywhere inside their bounds while Select is active.
- In Select mode, left-drag empty board space to marquee-select multiple objects. Hold `Shift`, `Ctrl`, or `Cmd` to add to the existing selection.
- Drag one selected object to move the complete multi-object selection together.
- In Pan mode, left-drag anywhere to move the viewport without moving or selecting objects.
- Hold `Space` while dragging, or use the middle mouse button, to pan temporarily from any tool. Trackpad scrolling also pans; `Ctrl/Cmd + wheel` zooms at the pointer.
- Select an object to reveal contextual actions, resize handles, and—where applicable—a connector handle.
- Double-click a note or press `Enter` while selected to edit. Double-click a sticker or press `Enter` while it is selected to change it.
- Use the board switcher to create, rename, duplicate, delete, and search boards.
- Use Export for current-board JSON, selected-object JSON, complete backups, clean PNGs, and browser-generated PDF/print output.

## Keyboard shortcuts

- `V` — Select tool
- `H` — Pan tool
- `N` — Create default sticky note
- `Shift + N` — Open note-template picker
- `S` — Activate the last-used sticker
- `Shift + S` — Open sticker picker
- `T`, `P`, `C`, `F` — Text, Pen, Connector, Frame
- `Space + drag` — Temporarily pan from any tool
- `Ctrl/Cmd + Z` — Undo
- `Ctrl/Cmd + Shift + Z` — Redo
- `Ctrl/Cmd + C`, `Ctrl/Cmd + V` — Copy and paste
- `Ctrl/Cmd + D` — Duplicate selection
- `Ctrl/Cmd + F` — Search
- `Ctrl/Cmd + S` — Force local save
- `0`, `1` — Reset view and fit content
- `Delete` or `Backspace` — Delete selection

## Kanban template

The Kanban structured note includes:

1. Ticket #
2. Ticket Type: Story, Bug, Subtask
3. Sprint #
4. Epic
5. Description
6. Team: SPA, PIC, PPD, CPPD, FES, R&A, P&BA, CMDSPT, HCM, SEC, EEO
7. Reporter
8. Assignee
9. Status: Backlog, VP Scheduled, VP Held, Ready, In Dev, UAT, Done
10. Needs VP?
11. Need By Date

Kanban notes support expanded and compact views, field-aware search and filters, clean exports, conversion to blank notes, duplication, color changes, connectors, and local autosave.

## Data and privacy

- Data is stored locally in IndexedDB, with a localStorage fallback.
- No account, server, telemetry, analytics, ads, or third-party tracking is included.
- Use **Complete Backup JSON** regularly for portable backups.
- Imported JSON is validated before it changes the workspace.

## Files

- `index.html` — self-contained application with embedded CSS and JavaScript
- `sw.js` — small offline app-shell cache for static hosting
- `README.md` — usage and deployment notes

## Browser notes

TACKBOARD targets current versions of Chrome, Edge, Firefox, and Safari. PDF export opens a clean print view; choose **Save as PDF** in the browser print destination. For large boards, use **Entire Board — Tiled Pages** to preserve readability.
