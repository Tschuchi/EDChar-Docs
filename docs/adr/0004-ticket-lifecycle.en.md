# ADR 0004: Ticket lifecycle with a "Next" field and a testing gate

**Status:** Accepted, extended in several steps (2026-06-27 to 2026-11-01)

## Context

Instances that cannot see each other need to know whose turn it is and how far a ticket has progressed. At the start, the board only knew three states: Open, In progress, Done. The implementing instance set "Done" itself.

## Decision

Every ticket has a status and a "Next" field.

- **"Next"** names who should look at the ticket next: an instance, Thore Schuchardt, or nobody. An instance that is waiting only reacts to tickets with its own name in this field. Introduced on 2026-06-29.
- **Lifecycle:** Open → In progress → Test (Testing) → Acceptance (Thore) → Release → Archived.

The lifecycle grew from incidents and new roles:

| Date | Change |
|---|---|
| 2026-07-04 | Implementing instances set "Test" instead of "Done". Only the Board-Keeper archives, after confirmation by Thore Schuchardt. |
| 2026-07-18 | New status "Release": approved on the build server, but not live yet. Reason: tickets 38–41 and 43–47 had been approved but were not live. |
| 2026-07-19 | Testing instance checks tickets automatically on the build server and records a result (tickets 55, 56). |
| 2026-07-20 | Lifecycle with "In progress" and "Waiting for approval"; the status "Test failed" is dropped (tickets 65–68). |
| 2026-10-29 | Each ticket gets a field "test approach" (UI, API, unit, analysis). |
| 2026-10-30 | Status names made explicit: "Test (Testing)" and "Acceptance (Thore)". |
| 2026-11-01 | Status "Permanent task" for tickets that are never archived (tickets 27, 76). |

Analysis tickets skip testing and go straight to acceptance by Thore Schuchardt. "Release" is set only after Thore Schuchardt has confirmed the result on the build server.

## Rejected alternatives

No alternatives are recorded on the board. The first lifecycle (Open → In progress → Done, set by the implementing instance) was replaced.

## Consequences

- Every step has an owner, and handovers are visible in the history of each ticket.
- Testing returned 8 of 92 tested tickets with at least one failed result (see [Facts and figures](../showcase/facts.md)).
- Thore Schuchardt is the gate for acceptance and release, see [ADR 0002](0002-control-model.md).

## Sources

First version of the board (2026-06-27); board commit introducing the "Next" field (2026-06-29); board commits of 2026-07-04, 2026-07-18, 2026-10-29, 2026-10-30, 2026-11-01; tickets 27, 48, 55, 56, 65–68.
