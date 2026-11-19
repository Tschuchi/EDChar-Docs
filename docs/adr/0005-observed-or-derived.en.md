# ADR 0005: Label every finding as "observed" or "derived from the code"

**Status:** Accepted (2026-10-29)

## Context

Agents read a lot of code and draw conclusions from it. A conclusion from code reads like a fact, but has not been checked against the running system.

## Decision

On 2026-10-29 the same rules were added to the CLAUDE.md of all instances:

1. Every finding on the board and in answers is labelled either **observed** (backed by an actual call, test or recording) or **derived from the code**. Derivations are never stated as facts.
2. Before a reported bug is fixed, it is reproduced with a real call on the build server, and the evidence goes into the ticket. If it cannot be reproduced, the ticket gets a question for the author and is not fixed.
3. If a finding contradicts what the author observes in production, the contradiction is named and clarified before anything changes.
4. A new bug ticket whose error has not been observed yet goes to Testing first, not to the instance that would fix it. Testing reproduces the error and then hands the ticket on.

## Rejected alternatives

No alternatives are recorded on the board.

## Consequences

- Reports on the board distinguish between what was seen and what was concluded, often line by line.
- Bugs found only in code analyses (for example in ticket 137) pass through Testing before anyone fixes them. Rule 4 was introduced while working on ticket 142, a finding from that analysis.
- The rule also applies to this documentation: numbers and statements are marked accordingly.

## Sources

CLAUDE.md of the board, Frontend, Backend and Testing (2026-10-29); tickets 137, 142.
