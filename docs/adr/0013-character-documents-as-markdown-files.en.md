# ADR 0013: Character documents as Markdown files instead of database records

**Status:** Accepted (2026-09-06)

## Context

Players wanted to keep any number of freely named text documents per character, for example a background story, notes on artefacts or running notes, without fixed categories. Thore Schuchardt described the feature in a requirements document on 2026-09-06.

## Decision

Documents are stored as Markdown files on the server, not in the database. Each character gets its own folder, each document is one `.md` file. The backend provides endpoints to create, list, rename, delete and save documents, with autosave (ticket 114). Images are uploaded separately and referenced from the Markdown text by a relative path (ticket 115).

## Rejected alternatives

- **Storing documents in the database:** named as excluded in ticket 114. The reasons are not recorded on the board.
- **Download and re-upload of single documents as files:** deliberately rejected and out of scope.

## Consequences

- The editor works on plain Markdown text, see [ADR 0014](0014-own-markdown-editor.md).
- Because single documents cannot be downloaded or uploaded, nobody edits the files by hand. Normalising the Markdown therefore does no harm.

## Sources

Tickets 114, 115, 117.
