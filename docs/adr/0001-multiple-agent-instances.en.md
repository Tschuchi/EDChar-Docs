# ADR 0001: Several Claude Code instances with separate repositories

**Status:** Accepted, extended over time (2026-06-27 to 2026-11-19)

## Context

EDChar consists of a Flutter web app and a PHP backend in two repositories. Both were developed with Claude Code. Each Claude Code session works in one folder and does not see what another session is doing.

## Decision

Every part of the system gets its own Claude Code instance, with its own repository, its own CLAUDE.md and its own permissions. The instances never talk to each other directly. A shared ticket board in its own repository is the only channel between them (see [ADR 0003](0003-markdown-board-in-git.md)).

The setup grew in steps:

| Date | Instance | Role |
|---|---|---|
| 2026-06-27 | Frontend, Backend | Implement in their own repository |
| 2026-07-02 | Board-Keeper | Maintains the board, creates and archives tickets, never merges |
| 2026-07-19 | Testing | Tests on the build server, reports results, own test repository (tickets 55, 56) |
| 2026-11-19 | Docs | Writes the public documentation, reads all other repositories (ticket 238) |

Each instance has a clear boundary. The frontend CLAUDE.md, for example, says: no backend code, no assumptions about backend behaviour; if a change needs a new or changed backend field, name it instead of guessing. Since 2026-11-06 Frontend and Backend each work in their own clone of the board repository, Docs since its start.

## Rejected alternatives

No alternatives are recorded on the board.

## Consequences

- A change that affects both sides needs a ticket for each side. The protocol requires filling in a cross-repository note and creating a ticket for the other side.
- Mismatches surface at the boundary. The contract audit in ticket 8 found mismatched field names in many endpoints (tickets 9–17), see [ADR 0011](0011-charkey-at-the-interface.md).
- Work only moves when the human starts it, see [ADR 0002](0002-control-model.md).

## Sources

First commit of the board (2026-06-27); CLAUDE.md of the Board-Keeper (2026-07-02); tickets 55, 56, 238; frontend CLAUDE.md, rule "repository boundary"; CLAUDE.md of Frontend and Backend, own board clone (2026-11-06).
