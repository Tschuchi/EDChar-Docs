# Testing

Code passes several checks before it reaches the live server. Some run automatically in the pipelines, others are done by the Testing instance, and the last one is Thore Schuchardt's acceptance on the build server.

## The layers

| Layer | Who | What | When |
|---|---|---|---|
| Static analysis and unit tests (frontend) | Frontend pipeline | `flutter analyze` and 256 unit and widget tests, on the CI runner | every push |
| API test suite (backend) | Backend pipeline | 649 checks against the build server: authentication, ownership, response formats, happy paths | after every deploy to build |
| Live lock (backend) | Backend pipeline | A push to `main` is first deployed to build and tested; the live deploy only starts if the suite is green | every GoLive |
| Ticket check | Testing instance | UI tests with Playwright, API calls, review of CI runs and tests, depending on the ticket's test approach | every ticket with status "Test (Testing)" |
| GoLive check | Testing instance | Everything noted in the release collection as "check before GoLive" | before every GoLive |
| Acceptance | Thore Schuchardt | Manual check on the build server | every ticket before "Release" |

Numbers: status 2026-11-23 (API checks per run: 2026-11-07), see [Facts and figures](facts.md). Design decisions: [ADR 0008](../adr/0008-api-tests-after-every-deploy.md) (API tests) and [ADR 0009](../adr/0009-ui-tests-with-playwright.md) (UI tests).

## Who writes which tests

Frontend and Backend write the unit and API tests in their own repositories. Testing does not write app code. It checks the tickets independently and reviews whether tests were weakened. Its own Playwright scripts live in the testing repository (42 scripts as of 2026-11-23).

## How Testing checks a ticket

Each ticket has a **test approach**: UI, API, unit or analysis. Testing chooses its method accordingly.

1. **Probe suite.** At the start of each round, a small suite checks that the test setup itself works.
2. **Check on build.** Testing signs in with two dedicated test accounts and checks the acceptance criterion of the ticket. It never tests against the live server, except read-only calls without sign-in.
3. **Result with evidence.** Testing records a table in the ticket: check, expected, received, OK or deviation, and whether the evidence is observed or derived from the code. Screenshots and logs go into the testing repository.
4. **Handover.** Passed: Acceptance (Thore), Next: Thore. Failed: back to In progress, Next: the implementing instance.

[One ticket, end to end](end-to-end.md) shows such a result table.

## Reproducing bugs

A bug that was only derived from the code goes to Testing first, not to the instance that would fix it. Testing reproduces it on the build server, and only then is it fixed. The rule came from findings that turned out to be intended behaviour or no bug at all (see [ADR 0005](../adr/0005-observed-or-derived.md) and [Incidents](incidents.md#a-bug-that-could-not-happen)).

## Results

- Testing returned 8 of 92 tested tickets with at least one failed result (derived from the archive, approximate).
- Thore Schuchardt returned about 10 tickets after his own check on build.

See [Facts and figures](facts.md#effectiveness) for method and limits.

## Credentials

The test accounts' credentials are stored outside the repositories: as secrets in the pipelines and in a local file that is excluded from Git. Before Testing commits scripts or evidence, a check scans them for credentials.
