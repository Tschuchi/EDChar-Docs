# Rules and why they exist

Every instance works under a CLAUDE.md file that defines its role, its permissions and its procedures. Most rules in these files were added later, in response to a specific incident or decision. This page collects them with their origin.

The CLAUDE.md files are written in German. The excerpts below are shortened English translations, not complete copies. Where it helps, the German original is quoted. Dates and commits come from the git history of the CLAUDE.md files, ticket numbers from the ticket archive. Where the board does not record an incident behind a rule, this is stated.

## Coordination

### The board is the only channel

> Before editing the board: pull. After editing: commit and push immediately.

**Since:** 2026-06-27, the first version of the board.
**Why:** The instances work in separate repositories and cannot see each other. The board file is the only place where they exchange status, blockers and cross-repository dependencies.

### Only the Board-Keeper archives

> Frontend and Backend set a ticket to "Test" after implementing it, never to "Done". Archiving is done exclusively by the Board-Keeper.

**Since:** 2026-07-04.
**Why:** No recorded incident on the board. The rule separates "implemented" from "confirmed by Thore Schuchardt" from "live".

### "Release" between approval and go-live

> "Release" means confirmed on the build server but not yet live. "Done" means live and finally confirmed.

**Since:** 2026-07-18.
**Why:** Tickets 38–41 and 43–47 had been approved, but were not live yet. They were moved back to the new status "Release".

### No merge to main without a release ticket

> Merges to main are only allowed through a documented release ticket.

**Since:** 2026-07-18, ticket 48.
**Why:** Version v2.1.24.0 was found running live, but no release ticket documented the merge that put it there. See [Incidents](incidents.md#an-undocumented-merge-to-main).

### Re-read the board before every status report

> `git pull` only updates the file on disk, not my conversation context. Before every status report, the board must be read again after the pull. Never rely on the state from earlier turns.

German original: *"git pull aktualisiert nur die Datei auf der Platte, nicht meinen Gesprächskontext."*

**Since:** 2026-07-19, Board-Keeper.
**Why:** The rule text names the cause: an instance that has pulled still answers from what it read earlier in the conversation. The board does not record the specific incident as a ticket.

### Own clone of the board for Frontend and Backend

> The board is kept in the instance's own clone of the board repository. Pull there before every change, push right after it.

**Since:** 2026-11-06, Frontend and Backend. Docs started with its own clone on 2026-11-19.
**Why:** Until then, Frontend and Backend worked in one shared folder. Thore Schuchardt recalls that Backend regularly reported no tickets for itself although a ticket with "Next: Backend" existed, and that this stopped after the change (Thore Schuchardt's account). See [Incidents](incidents.md#no-tickets-for-me-although-there-were).

### Formal corrections without asking

> Formal gaps and contradictions in tickets (repository, test approach, outdated notes) are corrected by the Board-Keeper and reported afterwards. Questions to Thore Schuchardt are only for decisions on content: scope, priority, variants, security.

**Since:** 2026-11-02, together with formal corrections to tickets 170, 187 and 189.
**Why:** It keeps Thore Schuchardt out of the loop for bookkeeping and in the loop for decisions.

## Evidence

### Observed or derived from the code

> Every finding is labelled either "observed" (backed by an actual call, test or recording) or "derived from the code". Derivations are never stated as facts.

German original: *"beobachtet" … "aus dem Code abgeleitet"*

**Since:** 2026-10-29, added to all instances on the same day.
**Why:** The backend version adds two related rules: a reported bug is reproduced on the build server before it is fixed, and a finding that contradicts what Thore Schuchardt observes in production is clarified before anything changes. Thore Schuchardt recalls a bug in a popup that Testing had derived from the code, but that could not occur in the app, and other derived anomalies that turned out to be intended behaviour (Thore Schuchardt's account). See [Incidents](incidents.md#a-bug-that-could-not-happen).

### Unobserved bugs go to Testing first

> New bug tickets whose error has not been observed yet get "Next: Testing" instead of the instance that would fix them. Testing reproduces the error and then hands the ticket on.

**Since:** 2026-10-29, introduced while working on ticket 142.
**Why:** Ticket 142 was a finding from the code analysis in ticket 137. With this rule, a bug derived from code is reproduced before anyone fixes it.

## CI and deployment

### Read the CI result yourself

> After every push, wait for the Actions run and read the result. Set a ticket to "Test (Testing)" only when the run is green.

**Since:** 2026-11-02, Frontend and Backend.
**Why:** No recorded incident on the board.

### No empty commits to restart a run

> Do not push an empty commit to restart a run. If a run needs a restart without code changes, ask Thore Schuchardt to restart it in Actions.

**Since:** 2026-11-02, Backend.
**Why:** No recorded incident on the board. Ticket 215 later documented that backend runs often failed on infrastructure (a timeout while resetting test data) rather than on tests.

## Versions and GoLive

### One version number per GoLive

> The readable version number exists only per GoLive and is kept in one place. Builds in between are identified by a build ID. The changelog collects changes under "Unreleased (Build)".

**Since:** 2026-11-07, ticket 229.
**Why:** Before, every build had its own number. Ticket 224 records four version collisions between Frontend and Backend. An intermediate rule from 2026-11-05 required reserving each number on the board before using it. Ticket 229 replaced it.

### Backend goes live first

> Order: Backend first, then Frontend. Backend changes are backwards compatible, new frontend versions often need the new backend.

German original: *"Backend-Änderungen sind rückwärtskompatibel, neue Frontend-Stände brauchen oft das neue Backend (Vorfall GoLive v2.3.12.0)."*

**Since:** 2026-11-07.
**Why:** The GoLive of v2.3.12.0. See [Incidents](incidents.md#golive-v23120-frontend-before-backend).

### GoLive takes precedence, only tested code goes live

> "GoLive" interrupts the current ticket. Work in progress stays local and is neither pushed nor merged during the GoLive. Only a state that Testing has checked is merged.

**Since:** 2026-11-07, Frontend and Backend.
**Why:** No recorded incident on the board. The rule was added on the day of the change to the GoLive order.

## Code

### Naming boundary between frontend and backend

> The Dart side uses camelCase, the PHP backend uses snake_case. This is not converted automatically. Before using a new or changed API field name, confirm the exact name from the API contract.

**Since:** 2026-06-27, frontend CLAUDE.md, the same time as the first tickets on the board.
**Why:** The rule itself lists known mismatches (`hasKey`/`has_key`, `apiKey`/`api_key`). The contract audit in ticket 8 found mismatched field names in many more endpoints (tickets 9 to 17). See [Incidents](incidents.md#field-name-mismatches-between-frontend-and-backend).

## Environment

### Run `cd` and git as separate commands

> When working outside the own project folder, run `cd` and the following git commands as separate tool calls, not chained.

**Since:** 2026-06-28, Frontend and Backend.
**Why:** The frontend rule text states it: chained `cd` commands always trigger a manual confirmation, regardless of the permissions in `settings.json`. Separate commands use the permissions that were granted.
