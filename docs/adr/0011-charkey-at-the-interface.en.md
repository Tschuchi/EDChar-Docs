# ADR 0011: `charKey` as the standard name at the interface, database columns unchanged

**Status:** Accepted (2026-11-02, 2026-11-06)

## Context

Frontend and backend had used different names for the same fields from the start. The contract audit in ticket 8 found mismatches in many endpoints (tickets 9–17). The code analysis in ticket 137 counted three spellings of the character key: `charKey` in 92 files, `character_key` in 46 and `characterKey` in 38. Each endpoint expected its own name. A different name led to an empty key, one of the causes of ticket 168.

## Decision

1. **At the interface (ticket 195):** A central helper accepts the character key under all spellings. `charKey` is the standard name.
2. **In the database (ticket 196):** The columns are not renamed. `charKey` stays the standard at the interface, the column names are internal.

## Rejected alternatives

From the analysis in ticket 196:

- **Align only one table:** small effort, but the split between `charKey` and `character_key` would remain.
- **Rename everything to `charKey`:** 9 tables, about 100 SQL strings in about 60 files, import translation, aliases or coordinated frontend changes, migration and rollback script; estimated 2–3 backend tickets. Medium to high risk, a maintenance window would be needed, and errors would only show up as SQL errors in single endpoints.

## Consequences

- New code uses `charKey`. Old spellings keep working.
- Endpoints that return whole rows still return `character_key`. This is documented in the API contract.
- The frontend CLAUDE.md requires confirming every field name against the API contract (naming boundary between camelCase in Dart and snake_case in PHP).

## Sources

Tickets 8–17, 137, 168, 195, 196 (options and decision of 2026-11-06); frontend CLAUDE.md, rule "naming boundary".
