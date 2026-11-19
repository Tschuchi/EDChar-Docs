# Facts and figures

**Cut-off date: 2026-11-19.** All numbers were counted from the repositories, the ticket board (`TICKETS.md`) and the ticket archive (`TICKETS_ARCHIV.md`) on that date. Each number states its source and method.

Labels used on this page:

- **counted:** determined directly by counting files, headings or commits.
- **derived from the archive, approximate:** determined by pattern matching in ticket texts. The archive was not kept in a uniform format over time, so these numbers have known limits, which are listed next to them.

## Project

| Figure | Value | Source and method |
|---|---|---|
| First commit | 2026-04-23 | Frontend and backend repositories, `git log --reverse` (counted) |
| Ticket board started | 2026-06-27 | First commit of the coordination repository (counted) |
| Testing instance started | 2026-07-19 | First commit of the testing repository (counted) |
| Commits | Frontend 452, Backend 422, Board 1,191, Testing 59 | `git rev-list --count HEAD` on the current branch of each repository (counted) |
| Tickets | 241 | Ticket headings in board and archive. Numbers run from 1 to 243, numbers 23 and 24 were never used (counted) |
| Tickets archived | 222 | 220 done, 1 deferred, 1 dropped (counted) |
| Tickets on the board | 19 | Including 2 permanent tickets (release history and release collection) (counted) |
| Releases (GoLives) | 32 | Entries marked "Release" in the backend changelog, first v2.1.21.0 on 2026-07-02, latest v2.4.0 on 2026-11-08 (counted) |
| Version entries | 235 | All version headings in the backend changelog, including intermediate build versions (counted) |
| UI languages | 2 | English and German, one ARB file each in the frontend (counted) |

## API

| Figure | Value | Source and method |
|---|---|---|
| Documented endpoints | 201 | Headings of the form `METHOD /path` in the API contract (counted) |
| Distinct endpoint paths | 183 | Same headings, unique paths. Some paths accept more than one method (counted) |
| PHP files | 203 | All `.php` files in the backend except tests, scripts and templates. This includes shared helpers, so it is an upper bound for endpoints (counted) |

## Tests

| Figure | Value | Source and method |
|---|---|---|
| Frontend unit and widget tests | 254 test cases in 19 files | `test(` and `testWidgets(` calls in `*_test.dart` (counted, static) |
| API test suite | 1 script, about 400 check calls in the source | `expect`/`check` calls in the suite (counted, static; loops produce more checks at runtime) |
| API checks per run | 649 | Result of a CI run against the build server, recorded on the board on 2026-11-07 (observed by the backend instance) |
| UI test scripts (Playwright) | 41 | `test_*.py` files in the testing repository (counted) |

## Effectiveness

These figures describe how work moved through the ticket workflow.

| Figure | Value | Source and method | Limits |
|---|---|---|---|
| Returns by Testing | 8 of 92 tested tickets | Archived tickets with a field "Testing-Ergebnis" (testing result) and at least one ❌: tickets 74, 151, 171, 186, 195, 198, 204, 210 (derived from the archive, approximate) | The field exists from ticket 55 (2026-07-19) on. Before that, testing was done by the author. For ticket 151 the ❌ covered only the first of several steps. |
| Returns by the author after testing on build | about 10 | Notes like "test result (author): ❌" or "error persists" (tickets 43, 75, 77, 81, 101, 104, 105, 111, 117, 118) (derived from the archive, approximate) | Free-text notes. Returns without these phrases are not counted. |
| Bug tickets | 41 | Archived tickets with "Bug" in the title (counted) | Bugs filed under other titles (e.g. "Fix", "UX") are not included. |
| Bugs by finder | Testing 17, author 11, Frontend/Backend 4, unclear 9 | Keyword classification of each bug ticket's context field (derived from the archive, approximate) | The finder is not a field of its own. The classification uses the first matching keyword and can be wrong for individual tickets. |
| Reopened tickets | 0 reopened after done, 2 reactivated after being deferred | Markers "reactivated" or "reopened" (tickets 64, 84) (derived from the archive, approximate) | Follow-up work is usually filed as a new ticket, so the number of reopened tickets understates rework. |
| Lead time, open to live | median 1 day, mean 5.2 days, middle half 1–6 days, maximum 66 days (217 of 222 tickets) | Start: first commit in which the ticket heading appears in `TICKETS.md`. End: field "Erledigt am" (done on) in the archive (derived from the archive, approximate) | The end date is the go-live date, not the date of the "Release" status. Five tickets have no usable date. |
| Share of analysis tickets | 17 of 222 (8 %) | "Analysis" in the title or in the field "Testansatz" (test approach) (derived from the archive, approximate) | The field "Testansatz" exists only since 2026-10-29. Earlier analysis tickets count only if the title says so. |
| GoLives | 32 | See "Releases" above (counted) | |

!!! info "Not on the board"
    Costs (subscriptions, tokens) and the time spent are not recorded on the board and are therefore not listed here.
