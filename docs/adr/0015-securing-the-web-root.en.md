# ADR 0015: Securing the web root

**Status:** Accepted (2026-10 to 2026-11)

## Context

The backend is deployed by copying the repository content into the web root of the hosting. The architecture and code quality analysis in ticket 137 looked at what this means for files that are not meant for the web:

- **Configuration file:** The file with the database credentials lay inside the web root, and the repository's access rules did not block dotfiles. From this the analysis derived that the file could be reachable over the web (derived from the code and the configuration).
- **Other files:** Documentation and Markdown files, a Python script and package manager files were readable over the web (observed by the backend instance). An unused folder with old code was deployed as well.

Later the pipeline was found to also upload the folder with the Claude Code settings (observed while working on ticket 215; content harmless, no credentials).

## Decision

- **Block files that are not meant for the web:** dotfiles, Markdown, Python and shell files, package manager files, and direct access to the library and script folders (tickets 139, 140).
- **Keep the configuration outside the web root:** as part of this security screening, the configuration file was moved out of the web root regardless of the existing access rules. The API reads it from a folder outside the web root, separately for build and live. The old location stays as a fallback, so nothing breaks while the file is being moved (ticket 140).
- **Replace credentials as a precaution:** all affected passwords and access credentials were replaced (Thore Schuchardt's account).
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

Tickets 137 (analysis), 139 (blocking dotfiles), 140 (configuration outside the web root, further blocks), 215, 216 (decisions of 2026-11-05), 217; Thore Schuchardt's account of 2026-11-20 on replacing the credentials.
