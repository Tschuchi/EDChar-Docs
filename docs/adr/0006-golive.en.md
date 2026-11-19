# ADR 0006: GoLive – the instances merge themselves, backend first

**Status:** Accepted (2026-07-20); order changed on 2026-11-07

## Context

Frontend and backend each deploy to the build server on every push to `develop` and to the live server on every merge to `main`. A release therefore means two merges in two repositories, plus a version number and a changelog entry. Until July 2026 the author merged to `main` himself, after Frontend had set the version and Backend had written the changelog entry.

On 2026-07-18 version v2.1.24.0 was found running live, but no release ticket documented the merge that put it there (ticket 48). From then on, merges to `main` were only allowed through a documented release ticket.

## Decision

Since 2026-07-20 a release is triggered by the command word **"GoLive"**. The author no longer merges anything himself. The instances merge on their own, one after the other, and hand over through the "Next" field of ticket 27. Afterwards the Board-Keeper archives all tickets of the release collection ticket 76.

Later additions:

- **2026-11-06, GoLive preparation:** Before a GoLive, Testing checks everything noted in ticket 76 as "check before GoLive" and reports back to the author.
- **2026-11-07, order:** Backend goes first, then Frontend. Backend changes are built to be backwards compatible, while new frontend versions often need the new backend. The author sends "GoLive" to Backend.
- **2026-11-07, precedence:** "GoLive" interrupts the current ticket. Work in progress stays local and is neither pushed nor merged during the GoLive. Only a state that Testing has checked is merged.

## Rejected alternatives

- **The author merges manually:** practice until 2026-07-20, replaced by the command word.
- **Frontend first:** order from 2026-07-20 to 2026-11-07. During the GoLive of v2.3.12.0 the frontend went live before the backend. Until the backend followed, a failed login could be shown as a success (derived from the code, as recorded on the board).

## Consequences

- A GoLive is a chain of handovers on the board: Backend → Frontend → Board-Keeper.
- The version number of a GoLive is set by the Board-Keeper, see [ADR 0007](0007-one-version-per-golive.md).
- Changes must be backwards compatible on the backend side, because the backend is live before the matching frontend.

## Sources

Tickets 27, 48, 65–68, 76; board commits of 2026-07-18 and 2026-07-20; CLAUDE.md of the Board-Keeper, Frontend and Backend (2026-11-06, 2026-11-07); GoLive v2.3.12.0 in ticket 27.
