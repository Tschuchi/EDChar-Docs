# ADR 0012: Characters are linked to their owner by user ID, not by e-mail address

**Status:** Accepted (2026-07-21)

## Context

Characters were linked to their owner through the e-mail address. Ownership checks compared the address on the character with the address of the user. The endpoint for changing the e-mail address only updated the user, not the characters. After a change, the user's characters would have become invisible and inaccessible (derived from the code). The planned feature "change e-mail" (ticket 75) would have made this bug reachable for every user.

## Decision

Characters get a user ID column that refers to the user. All affected endpoints check ownership by user ID. The migration was done before the e-mail feature was built. The pattern of linking by user ID already existed elsewhere in the schema.

## Rejected alternatives

No alternatives are recorded on the board. The analysis in ticket 70 covered the effort and risks of the change. Thore Schuchardt then decided to implement it.

## Consequences

- Changing the e-mail address does not affect the characters.
- Before the migration, characters without a matching user had to be identified and clarified with Thore Schuchardt.

## Sources

Tickets 70 (analysis, decision of 2026-07-21), 74 (migration), 75 (feature "change e-mail").
