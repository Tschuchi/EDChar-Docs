# Incidents

Incidents from the ticket archive and the history of the CLAUDE.md files that led to a rule or a lasting change. Each entry states what happened, where it is recorded and what changed. Facts only, no evaluation.

## Field name mismatches between frontend and backend

**What happened:** The frontend and the backend used different names for the same fields. A contract audit (ticket 8) compared the frontend code with the API contract and found mismatches in many endpoints, for example for passwords, API keys, chat, documents and the character key (tickets 9 to 17). Later, the code analysis in ticket 137 counted three spellings of the character key: `charKey` in 92 files, `character_key` in 46 and `characterKey` in 38. A different name led to an empty key, which was one of the causes of ticket 168.
**Recorded in:** tickets 8–22, 137, 168, 195.
**Resulting rule:** Naming boundary in the frontend CLAUDE.md since 2026-06-27 (confirm every field name against the contract). Ticket 195 made `charKey` the standard and the backend accepts all spellings in one central place. Ticket 196 decided not to rename the database columns.

## Changing the e-mail address would have hidden the characters

**What happened:** Characters were linked to their owner by the e-mail address. Changing the e-mail address updated the user, but not the characters. All ownership checks compared the addresses, so after a change the characters would have become inaccessible (derived from the code). The planned feature "change e-mail" (ticket 75) would have made this bug reachable for every user.
**Recorded in:** tickets 70 (analysis) and 74 (migration).
**Resulting change:** Characters are linked by user ID instead of e-mail address. The migration was done before the e-mail feature was built.

## Approved, but not live

**What happened:** Tickets 38–41 and 43–47 had been approved by Thore Schuchardt, but were not live yet.
**Recorded in:** board commit of 2026-07-18.
**Resulting rule:** New status "Release" between approval on the build server and the go-live.

## An undocumented merge to main

**What happened:** Version v2.1.24.0 was running live, but no release ticket documented the merge to main. The Board-Keeper could not determine commit or date itself, because it has no access to the code repositories.
**Recorded in:** ticket 48, board commit of 2026-07-18.
**Resulting rule:** Merges to main only through a documented release ticket. Later replaced by the "GoLive" procedure (tickets 27, 65–68).

## "No tickets for me" although there were

**What happened (Thore Schuchardt's account):** Backend regularly reported that there were no tickets for it, although at least one ticket with "Next: Backend" was on the board. After the rule was introduced, this no longer happened.
**Recorded in:** There is no ticket for the incident. The rule names the mechanism: after `git pull` the file on disk is current, but the instance's conversation context still holds the older state.
**Resulting rule:** Read the board again after every pull before reporting status (CLAUDE.md of the Board-Keeper, 2026-07-19).

## A bug that could not happen

**What happened (Thore Schuchardt's account):** Testing reported a bug in a popup that it had derived from the code. The bug could not occur in the app, because at that point the popup could not be opened for such a character. More generally, anomalies derived from the code sometimes turned out to be intended behaviour or no bug at all.
**Recorded in:** There is no ticket for the incident.
**Resulting rule:** Label every finding as "observed" or "derived from the code", reproduce bugs on the build server before fixing them, and send unobserved bugs to Testing first (CLAUDE.md of all instances, 2026-10-29). See [ADR 0005](../adr/0005-observed-or-derived.md).

## Version collisions

**What happened:** Frontend and Backend each assigned version numbers for their builds. Ticket 224 records four collisions between them.
**Recorded in:** ticket 224, CLAUDE.md of Frontend and Backend (2026-11-05).
**Resulting rule:** First, each number had to be reserved on the board before use (2026-11-05). Two days later this was replaced by one number per GoLive plus a build ID (tickets 225–229).

## GoLive v2.3.12.0: frontend before backend

**What happened:** During the GoLive of v2.3.12.0 on 2026-11-07, the frontend went live before the backend (board commits at 02:46 and 02:58). The new frontend expected the new response format of the backend. Until the backend was live, a failed login could be shown as a success (derived from the code, as recorded on the board).
**Recorded in:** ticket 27 (release history), CLAUDE.md of the Board-Keeper, Frontend and Backend (2026-11-07).
**Resulting rule:** Backend goes live first, then Frontend.

## Overlapping pipeline runs

**What happened:** A deployment from main overwrote the build server while the tests of a develop run were still running. The develop run turned red (observed by the backend instance, 2026-11-07).
Thore Schuchardt recalls that backend runs often turned red when Frontend pushed at the same time (Thore Schuchardt's account). The board records overlapping backend runs. The frontend analysis in the same ticket found that frontend uploads do not touch the part of the server the backend tests use (derived from the code).
**Recorded in:** ticket 230.
**Resulting change:** Pipeline runs on the build server no longer overlap.

## Developer files served by the web server

**What happened:** The backend pipeline uploaded the `.claude` folder, so its settings file could be fetched over the web server. The content was harmless and contained no credentials (observed by the backend instance while working on ticket 215).
**Recorded in:** tickets 216 and 217.
**Resulting change:** Developer files are excluded from deployment. Ticket 217 checked the same for the frontend pipeline.
