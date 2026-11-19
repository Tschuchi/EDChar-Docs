# ADR 0014: Own Markdown editor instead of an editor library

**Status:** Accepted (2026-09-06)

## Context

The character documents (see [ADR 0013](0013-character-documents-as-markdown-files.md)) needed an editor with basic formatting, autosave, images, external links and jump marks to headings. The editor had to be native to Flutter, with no JavaScript editor embedded in the page, and fill the content area instead of opening in a popup. The app already used `flutter_markdown` for the changelog.

## Decision

The editor is built in-house: a native Flutter text field with a formatting toolbar. The buttons insert the Markdown syntax at the cursor, and images are uploaded through a toolbar button. Links and jump marks are handled by the app itself.

In a second step (ticket 118), the split between raw text and preview was replaced by a single writing surface. Formatting appears as you type and the Markdown characters stay hidden. What is stored remains plain Markdown.

## Rejected alternatives

- **`super_editor`:** only development versions were available, and its Markdown package was discontinued. Rejected in agreement with the author.
- **`appflowy_editor`:** chosen first and tried in a spike. The Markdown round trip kept the content but not the exact text (list markers and emphasis were normalised, the alt text of images was lost). The author accepted that. Shortly afterwards the author decided to switch to the in-house approach and to remove the library again. The reason for the switch is not recorded on the board.

## Consequences

- No dependency on an editor library.
- Inserting images by drag and drop or paste was dropped; images are inserted through the toolbar button.
- Further work on the editor followed: live formatting in ticket 118, and an open follow-up ticket 121 for remaining issues, for example with bullet and numbered lists (reported 2026-11-04).

## Sources

Tickets 117 (spike and decision of 2026-09-06), 118, 121.
