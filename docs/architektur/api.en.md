# API overview

The backend offers a JSON API under `/api/`. The web app is its only client. This page gives an overview of its areas and conventions. The reference for individual endpoints is the API contract in the backend repository, which is internal.

## Areas

Counted from the API contract on 2026-11-20: each heading of the form `METHOD /path` counts as one endpoint. Some paths accept both GET and POST, so the number of distinct paths is lower (183 in total).

| Area | Covers | Endpoints |
|---|---|---:|
| Accounts and sign-in | Registration, sign-in and sign-out, account data, changing e-mail and password, e-mail confirmation, password reset, game master role, accepting campaign invitations | 13 |
| Characters | Creating, loading, saving and deleting characters, circle advancement, comments on values, character documents, export and import, PDF export, character picture | 24 |
| Talents, skills, knacks, spells | Ranks per discipline, knacks, custom skills and spells, spell matrices, foreign spells through versatility, special talents | 55 |
| Other character parts | Legend points, karma, dice macros, animal companions | 18 |
| Equipment | Weapons, armor, other items | 18 |
| Reference data | Disciplines, races, passions | 9 |
| Campaigns, game master view | Campaigns, participants, invitations, sessions, legend point awards, modifiers, chat, broadcasts, documents, notes, AI assistant and its settings | 46 |
| Campaigns, player view | A character's campaigns and fellow travelers, chat with the game master, announcements, documents, modifiers, legend point awards, leaving a campaign | 16 |
| Meta | Build ID and changelog | 2 |
| **Total** | | **201** |

Reference data for talents, skills, spells and knacks is delivered by the endpoints of the respective character area.

## Conventions

| Topic | Convention |
|---|---|
| **Format** | JSON in both directions. Every response has `success` and either `data` or `error` (unified in tickets 154 and 155). |
| **Methods** | GET to read, POST to create, change or delete. Endpoints that change data enforce the method from the contract and answer 405 otherwise. |
| **Status codes** | 400 for missing or invalid parameters, 401 without a valid session, 403 for someone else's resource, 404 for unknown resources and for campaigns of other game masters, 405 for a wrong method, 500 for server errors. |
| **Session** | A PHP session cookie, set at sign-in. All endpoints except sign-in, registration, e-mail confirmation, password reset and the changelog require it. |
| **Character key** | `charKey` is the standard name for a character's key. The API also accepts the older spellings `character_key` and `characterKey` (see [ADR 0011](../adr/0011-charkey-at-the-interface.md)). |
| **Field names** | The API uses snake_case for most fields, the app camelCase. Names are not converted automatically and are checked against the contract. |
| **Language** | The app sends its language in the `Accept-Language` header; the API translates its messages accordingly (see [Multiple languages](i18n.md)). |
| **Access checks** | Shared checks for character ownership, animal companion ownership, game master role and campaign membership (see [Authentication and ownership](security.md)). |
| **Origins** | Requests are accepted only from the two app domains. |

## Tests

An automated suite checks the API against the build server after every deploy, including the 401 and 403 cases (see [Environments and CI/CD](environments.md)).
