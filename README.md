# Note App

A keyboard-only note-taking app that works entirely without a mouse. Designed for engineers and researchers, including users with low vision, it reimplements Obsidian-style note linking with a lower cognitive load.

## Target Users & Use Cases
Engineers and researchers. Intended for research notes, troubleshooting logs, meeting notes, and study logs.

## Main Features
- Reference links `[[...]]`, backlinks, and related-notes view
- Tags `::...::` with filtering
- Markdown formatting (CodeMirror 6-based: bold, italic, headings, checkboxes, etc.)
- Fuzzy-match autocomplete (Fuse.js)
- Overview modal (statistics, hub notes, potential links, isolated notes)
- Node graph with force-directed layout (notes sharing tags are placed closer together)

## Keyboard Operations
| Key | Action |
|---|---|
| Tab / Shift+Tab | Move focus |
| Enter | Confirm |
| Escape | Go back / cancel |
| Ctrl+S | Save |
| Shift+/ | Open overview modal |

## Design Decisions
- **No folder hierarchy**: Navigating nested folders imposes a high cognitive load for low-vision users, so a flat tag-based structure was used instead
- **CodeMirror 6**: Same foundation as Obsidian, with built-in ARIA support
- **Jaccard similarity for tag attraction**: Prevents notes with many tags from being over-attracted to unrelated notes, avoiding bias from raw tag counts
- **Separation of Overview Modal and Node Graph**: The text-based overview works regardless of vision; the node graph is a visual alternative for sighted users, using the Okabe-Ito color-blind-safe palette

## Known Limitations
- Screen reader testing has only covered the basic flow (navigation, note creation, editing)
- Search does not support hiragana-to-kanji matching, since it relies on string similarity (Fuse.js) rather than phonetic analysis

## Tech Stack
Vanilla HTML/CSS/JavaScript, CodeMirror 6, Fuse.js (both via CDN), localStorage, hosted on GitHub Pages

## Running Locally
```
python -m http.server 8000
```