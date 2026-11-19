# ADR 0010: Consolidating a grown API

**Status:** Accepted (2026-10 to 2026-11)

## Context

The backend had grown endpoint by endpoint. The code analysis in ticket 137 found:

- 192 files repeated the same header block (CORS, authentication, JSON header, database).
- 148 files checked the HTTP method themselves.
- About 48 game master endpoints each checked the game master permission on their own. A forgotten check would not have been noticed.
- 153 files returned a `success` field, the others only `error` or raw data.

## Decision

1. **Shared bootstrap:** All endpoints use one bootstrap file for CORS, authentication, method check and database. The game master check is central. Piloted in one area (ticket 145), then rolled out to all endpoints (ticket 151).
2. **Uniform response format:** All endpoints return the same format. Every endpoint that creates, changes or deletes something enforces the HTTP method named in the API contract (ticket 154).
3. **404 instead of 403 for other users' resources:** Deleting someone else's campaign answers 404, the same as an unknown campaign. The answer does not reveal whether the resource exists.
4. **Order of the change:** On the frontend, a shared request helper that understands both the old and the new format was introduced first (tickets 144, 149, 177–184). Twelve endpoints that the frontend read directly, including login, were switched last, in a fixed order: frontend to the helper, then backend, then removal of the old formats (ticket 155). Build and live must never have a state where login or similar does not work.

## Rejected alternatives

- **Parameter helper outside the game master area:** the helper for required parameters stays limited to game master endpoints, because elsewhere it would have changed the response format (decision of 2026-11-02).

## Consequences

- The migration needed the API test suite as a safety net, see [ADR 0008](0008-api-tests-after-every-deploy.md).
- The 404 behaviour is documented in the API contract.
- Before every GoLive, Testing checks the areas switched so far.

## Sources

Tickets 137, 144, 145, 149, 151 (decision of 2026-11-02), 154 (decisions of 2026-11-05 and 2026-11-06), 155 (order of 2026-11-06), 177–184.
