# ADR 0007: One version number per GoLive, plus a build ID

**Status:** Accepted (2026-11-06), in effect since the GoLive of v2.4.0 (2026-11-08)

## Context

Every build had its own readable version number. Each number needed a commit of its own and a full pipeline run of several minutes. Frontend and Backend assigned numbers independently, which led to four collisions. A rule from 2026-11-05 required reserving each number on the board before using it. In addition, the author wanted to see immediately on build and live whether he was using the latest version.

## Decision

Following the analysis in ticket 224:

1. The pipeline writes a **build ID** (date, time, short commit hash) into the app and the API on every deploy. The app shows both. No commit is needed just for a number.
2. A **readable version number** exists only per GoLive. The Board-Keeper assigns it (scheme vX.Y.Z, Z increases per GoLive; jumps in X or Y only by decision of the author). The first number in the new scheme was v2.4.0.
3. The changelog collects changes under a section "Unreleased (Build)". At the GoLive, Backend renames it to the new number. Old entries stay unchanged.
4. When the app is opened and after a successful sign-in, it checks whether the server delivers a newer version. If so, it reloads itself, including clearing the service worker and browser cache. It does not check while in use, because deployments do not run during use.
5. Cache headers make the browser check the app files before use.

The API reports its build ID through a dedicated endpoint.

## Rejected alternatives

- **Build ID in the changelog endpoint** instead of a dedicated endpoint.
- **Moving the intermediate changelog entries** into a separate place.
- **Checking for a new version before submitting the sign-in form** instead of after a successful sign-in.
- **Reserving numbers on the board:** the rule from 2026-11-05, replaced by this decision.

## Consequences

- No more commits just for version numbers, and no more collisions.
- Build and live always show which code is running.
- The steps were implemented in the order cache headers, build ID in the app, build ID in the API, check and reload, rule change (tickets 225–229).

## Sources

Tickets 224 (analysis and decisions of 2026-11-06), 225–229; CLAUDE.md of Frontend and Backend (2026-11-05, 2026-11-07); ticket 27.
