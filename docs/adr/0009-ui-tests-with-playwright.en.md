# ADR 0009: UI tests with Playwright and dedicated test accounts

**Status:** Accepted (2026-10-29)

## Context

The Testing instance controlled the author's Chrome browser through a browser extension. For security reasons the extension does not type credentials into login forms. The author would have had to sign in himself for every UI test and block calls by hand in the developer tools to test error cases. This contradicted the goal of automated tests with two test accounts.

## Decision

A spike (ticket 173) showed that Playwright can drive the app with automatic sign-in. The author decided that signing in through the login form is acceptable for automated tests. UI tests run with Playwright and two dedicated test accounts on the build server. The credentials stay outside the repositories.

## Rejected alternatives

- **Controlling the author's own browser through the extension:** previous practice, needed manual sign-in for every test.

## Consequences

- The testing repository contains 41 Playwright test scripts (see [Facts and figures](../showcase/facts.md)), with screenshots as evidence.
- Helpers were added for elements Playwright cannot find by text, for example icon buttons without a name (ticket 144).
- Screenshots for the handbook can be produced the same way (ticket 243).

## Sources

Tickets 144, 173 (spike and decision of 2026-10-29), 243.
