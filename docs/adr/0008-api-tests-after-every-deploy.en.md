# ADR 0008: Automated API tests after every deploy to the build server

**Status:** Accepted (2026-10-29); pipeline queue added on 2026-11-08

## Context

The code analysis in ticket 137 found that there were no API tests. The CI only checked PHP syntax and ran a PDF smoke test. Authentication and ownership checks were not covered. The planned migration of all endpoints to a shared bootstrap (see [ADR 0010](0010-consolidating-a-grown-api.md)) needed a safety net. The open design question was where the test data comes from.

## Decision

- An API test suite runs against the build server after every deploy.
- **Test data:** fixed test data (two test accounts with known campaigns and characters), plus a reset script that restores this state before every run. The script is not reachable over HTTP and refuses to run against any database other than the build database.
- **Live lock:** On a push to `main`, the main state is first deployed to the build server and tested. The live deploy only runs if the suite is green. There is no emergency bypass.
- **No overlapping runs (2026-11-08):** All runs that deploy to or test on the build server wait in a single queue instead of running in parallel or being cancelled.

## Rejected alternatives

- **Run the full invitation flow through the API on every run:** every run would send a real e-mail, and a mail server outage would block the live deploy although the code is fine.
- **A test endpoint on the build server for seeding data:** the code would also be deployed to live, protected only by configuration. A configuration error would open a backdoor.
- **Fixed test data without a reset:** an aborted run would leave the data in a changed state until someone fixes it by hand.

## Consequences

- A run checks 649 cases against the build server (recorded on the board on 2026-11-07).
- A red suite blocks the live deploy.
- Runs sometimes failed because of infrastructure, for example a timeout while resetting the test data, not because of the code (ticket 215).
- Before the queue existed, a deploy from `main` overwrote the build server while the tests of a develop run were still running, and that run turned red (ticket 230).

## Sources

Tickets 137, 146 (options and decision of 2026-10-29), 215, 230 (decision of 2026-11-08).
