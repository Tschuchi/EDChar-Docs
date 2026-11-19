# ADR 0015: Securing the web root

**Status:** Accepted (2026-10 to 2026-11)

## Context

The backend is deployed by copying the repository content into the web root of the hosting. The code analysis in ticket 137 showed that this also made files reachable over the web that were never meant to be: the configuration file with the credentials, documentation and Markdown files, a Python script, package manager files and an unused folder with old code. Later the pipeline was found to also upload the folder with the Claude Code settings (observed while working on ticket 215; content harmless, no credentials).

## Decision

- **Block files that are not meant for the web:** dotfiles, Markdown, Python and shell files, package manager files, and direct access to the library and script folders (tickets 139, 140).
- **Keep the configuration outside the web root:** the configuration file is read from a folder outside the web root, separately for build and live. The old location stays as a fallback, so nothing breaks while the file is being moved (ticket 140).
- **No internal error details to the client:** error texts go to the server log, the client gets a generic message (ticket 140).
- **Remove unused code:** the folder with old code was deleted after confirming that nothing referred to it (ticket 140).
- **Exclude developer files from the upload:** Claude Code settings, CLAUDE.md and workflow files are no longer deployed (ticket 216). The frontend pipeline was checked and uploads only the build output (ticket 217).

## Rejected alternatives

No alternatives are recorded on the board.

## Consequences

- Some blocked files answer with 403 instead of 404, because the server blocks every dotfolder, including ones that do not exist. This was accepted.
- The copy-based deploy does not delete anything on the server. Files removed from the repository must also be deleted on the server by hand.
- Moving the configuration file is a manual step on the server, done by Thore Schuchardt.

## Sources

Tickets 137, 139, 140, 215, 216 (decisions of 2026-11-05), 217.
