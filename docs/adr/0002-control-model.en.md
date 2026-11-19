# ADR 0002: Control model – the human owns decisions and the start signal, agents own execution

**Status:** Accepted (confirmed 2026-11-19)

## Context

With several agent instances (see [ADR 0001](0001-multiple-agent-instances.md)) the question is who starts work and who decides what is done. Agents could react to events on their own, or each step could be prompted individually.

## Decision

Thore Schuchardt deliberately keeps the role of the router between the instances.

- No instance starts without Thore Schuchardt's `scan` command. This is a pull signal: Thore Schuchardt decides whether and when work happens.
- All decisions on ticket content and scope, acceptance, release and GoLive, and the rules in the CLAUDE.md files stay with Thore Schuchardt.
- Within a scan, the instances keep working on their own until the board holds nothing more for them (since 2026-11-06).
- Control during execution comes from gates, not from individual prompts: a green CI run, the Testing instance, acceptance by Thore Schuchardt, the GoLive.

## Rejected alternatives

- **Event-driven automation:** agents react on their own to labels or webhooks.
- **Review only afterwards:** agents work freely and the code is reviewed later.

## Consequences

- Thore Schuchardt sets the pace and is a potential bottleneck.
- There is a risk that passing prompts between instances becomes routine.
- Where the tickets are stored does not change how autonomous the agents are (see [ADR 0003](0003-markdown-board-in-git.md)).

## Sources

Decision of Thore Schuchardt on 2026-11-19, recorded in ticket 240; rule "keep working until the board is empty" in the CLAUDE.md of Frontend and Backend (2026-11-06).
