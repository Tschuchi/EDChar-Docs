# One ticket, end to end

This page follows one real ticket from its origin to the live server: ticket 229, "Version rules: one number per GoLive, changelog 'Unreleased (Build)'".

**Why this ticket:** It has a history of incidents behind it, it involves Backend, Frontend, Board-Keeper and Testing as well as a decision by Thore Schuchardt, and it ends with a GoLive. Ticket 195 (the character key `charKey`) was the other candidate. It was a backend ticket, with the frontend side covered by a separate ticket, so it shows fewer handovers.

All times are taken from the commits on the board (counted). Commit hashes refer to the code repositories.

## Background

Until November 2026 every build had its own readable version number. Frontend and Backend assigned numbers independently, which led to four collisions. A rule from 2026-11-05 required reserving each number on the board before use. Thore Schuchardt also wanted to see at a glance whether build and live run the latest code. See [Incidents](incidents.md#version-collisions).

On 2026-11-06 the analysis ticket 224 laid out a target picture with options. Thore Schuchardt decided on three open points and the Board-Keeper created five implementation tickets, 225 to 229, in a fixed order: cache headers, build ID in the app, build ID in the API, check and reload, and finally the rule change. Ticket 229 had to wait until 225–228 were live. The full decision is in [ADR 0007](../adr/0007-one-version-per-golive.md).

## Timeline

| Time | Who | What happened | Status / Next |
|---|---|---|---|
| 2026-11-06 23:56 | Board-Keeper | Creates tickets 225–229 from the analysis in ticket 224 | Open, blocked until the GoLive with 225–228 |
| 2026-11-07 00:49 | Thore Schuchardt, Board-Keeper | Answers the open question: the app shows the number of the last GoLive plus the build ID. The acceptance criterion is adjusted. | |
| 2026-11-07 02:46–02:58 | Frontend, Backend | GoLive v2.3.12.0 with tickets 225–228; 229 is now unblocked | |
| 2026-11-07 03:05 | Backend | Starts the backend part | In progress, Next: Backend |
| 2026-11-07 03:13 | Backend | Changelog gets the section "Unreleased (Build)" at the top, the history stays unchanged. Backend CLAUDE.md updated (commits 40c5306, d8e826d). | Next: Frontend |
| 2026-11-07 03:20 | Board-Keeper | Removes the reservation rule from ticket 27; the GoLive number is now assigned by the Board-Keeper | |
| 2026-11-07 03:37 | Frontend | Starts the frontend part | In progress |
| 2026-11-07 03:48 | Frontend | Version only in `pubspec.yaml`, the app shows the GoLive number plus build ID; changelog note in ticket 27 without a number (commit 7545704) | Test (Testing), Next: Testing |
| 2026-11-08 01:34 | Backend | Transfers the frontend note into the changelog | |
| 2026-11-08 02:19 | Testing | Round 7: checks tickets 229, 230 and 231 on build | Acceptance (Thore), Next: Thore |
| 2026-11-08 02:23 | Thore Schuchardt, Board-Keeper | Acceptance; the remaining deviation in ticket 27 is fixed; GoLive number set to v2.4.0 | Release, in ticket 76 |
| 2026-11-08 02:38 | Backend | GoLive v2.4.0: changelog section renamed, merge to `main`, live checked | ticket 27 → Next: Frontend |
| 2026-11-08 02:53 | Frontend | GoLive v2.4.0: merge to `main`, live checked | ticket 27 → Next: Board-Keeper |
| 2026-11-08 02:55 | Board-Keeper | Archives tickets 229, 230, 231, empties ticket 76 | Archived |

From creation to live: about 27 hours, most of it waiting for the GoLive of the preceding tickets.

## The test result

Testing recorded its check as a table in the ticket. Shortened:

| Check | Expected | Received | Result | Evidence |
|---|---|---|---|---|
| Probe suite at the start of the round | green | 49 passed | OK | observed |
| Version line, player and game master view | "v2.3.12 · Build <hash> (<date>)", matching the build file on the server | matching | OK | observed (UI test) |
| No other number visible | only v2.3.12 | only v2.3.12 in the accessibility tree | OK | observed |
| Changelog in the app | "Unreleased (Build)" at the top, old history below | as expected | OK | observed (screenshot) |
| Changelog endpoint | new section at the top | as expected | OK | observed |
| Backend and frontend CLAUDE.md | no reservation or bump rule | only the note that both no longer exist | OK | derived from the code |
| Ticket 27 | no reservation or bump rule | old section "version scheme v2.1.X.Y" still present | deviation | observed |
| Test review | no weakened tests | tests only extended | OK | observed |
| CI | green | green in both repositories | OK | observed |

The deviation was not in Frontend's or Backend's work but in ticket 27, which is maintained by the Board-Keeper. Testing therefore passed the ticket on to acceptance instead of returning it, and noted the point for Thore Schuchardt. It was fixed before the release.

## What the example shows

- **Handovers run through the "Next" field.** No instance waited for a message. Each one found its next step on the board.
- **Order across repositories.** Backend went first, because the changelog section is where frontend notes are collected. The Board-Keeper had proposed that order in the ticket.
- **Decisions stay with the human.** The only open question went to Thore Schuchardt and was answered before the frontend part started.
- **Testing checks the rules, too.** Besides the app, Testing checked the CLAUDE.md files and the permanent ticket 27, and found the one remaining deviation there.
