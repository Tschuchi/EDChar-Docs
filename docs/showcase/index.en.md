# Showcase

Agentic development, using EDChar as the example.

EDChar was built by one person working with several Claude Code instances. Each instance has its own repository, its own CLAUDE.md and its own permissions. They do not talk to each other directly. A shared ticket board is the only channel between them.

!!! note "Work in progress"
    This section is being assembled. The fact sheet, the rules material and the incident list are available. The narrative pages are still to be written.

## Outline

| Page | Content | Status |
|---|---|---|
| Starting point | What EDChar is, why it was built this way, the situation before the multi-instance setup | planned |
| The setup: five instances | Frontend, Backend, Testing, Board-Keeper, Docs: responsibilities, repositories, what each may and may not do | planned |
| Ticket workflow and the "Next" field | Lifecycle from Open to Archived, how the "Next" field routes work between instances and the human | planned |
| CLAUDE.md as a working contract | How each instance's CLAUDE.md defines role, permissions and procedures | planned |
| [Rules and why they exist](rules.md) | Rules from the CLAUDE.md files, each with the incident or decision that led to it | material ready |
| GoLive | How a release goes live: preparation, order of the merges, checks on Live | planned |
| Testing | API tests after every deploy, UI tests with Playwright, the Testing instance as a gate | planned |
| [Facts and figures](facts.md) | Counts with method, source and cut-off date, including effectiveness metrics | ready |
| [Incidents](incidents.md) | Incidents that led to a rule: what happened, ticket, resulting rule | material ready |
| Lessons learned | Personal conclusions | planned (written by the author) |
| [Limits and transferability to teams](limits.md) | What does not carry over from a one-person setup | structure only |
