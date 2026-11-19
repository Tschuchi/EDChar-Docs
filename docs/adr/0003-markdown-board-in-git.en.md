# ADR 0003: Own Markdown board in Git instead of GitHub Issues or Jira

**Status:** Accepted; restructured on 2026-11-19

## Context

The instances need a shared place for tickets, status and cross-repository notes (see [ADR 0001](0001-multiple-agent-instances.md)). The board started on 2026-06-27 as a single Markdown file in its own Git repository.

## Decision

The board stays a set of Markdown files in Git.

- Agents read and write files natively, without an API and without a write token for a platform.
- Everything is versioned and there is no dependency on a platform.
- Fields and procedures match the process exactly: the "Next" field, the permanent ticket for versions and changelog (ticket 27), the release collection ticket (ticket 76).
- The archive also serves as the source for the showcase and for these ADRs.

## Rejected alternatives

- **GitHub Issues with Projects.** Advantages: targeted reading per agent via labels, links to commits, a ready-made board, a path to automation. Disadvantages: a write token per instance, a large migration, broken ticket numbers, issue types and issue fields only available for organisations, no enforced workflow.
- **Jira.** Oversized, separate from the code, needs another integration and further permissions.

The core argument: how autonomously the agents act does not depend on where the tickets are stored, but on what triggers them and which gates they pass. The main advantage of issues, automated routing, is deliberately not wanted (see [ADR 0002](0002-control-model.md)).

## Consequences

- **Known weaknesses:** On 2026-11-19 the single file had 226 KB with 20 active tickets, 139 KB of that in ticket 27 alone, because the history of the permanent tickets was never cleaned up. All instances wrote to the same file, which led to write conflicts. Since 2026-11-06 a separate board clone per instance has softened this.
- **Restructuring (decided and implemented on 2026-11-19):** An index file is now the only source for status fields, with one line per ticket. Each ticket has its own file for content and history. The history of the permanent tickets is moved to an archive at every GoLive. The old single-file archive stays unchanged as the source up to 2026-11-19.

## Sources

Decision of the author on 2026-11-19, recorded in ticket 240; structure of the board repository on 2026-11-19 (observed: index file, one file per ticket, archive folder with rotated histories).
