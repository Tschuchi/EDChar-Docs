# Authentication and ownership

## Sign-in and session

- **Registration** creates an account with e-mail address and password. The account can only sign in after the e-mail address is confirmed through a link.
- **Sign-in** checks the password against a stored hash. On success the server starts a PHP session and issues a new session ID. The session cookie is set with `SameSite=Lax`.
- **Same origin:** the app and the API are served from the same domain, so the browser sends the session cookie with every API call.
- **Session check:** every signed-in endpoint starts with the shared bootstrap. Without a valid session it answers with 401.
- **Password reset** works through a link sent by e-mail. The answer to the reset request does not reveal whether an address is registered.

## Origin check

The API only allows requests from the two app domains (build and live). POST requests from any other browser origin are rejected. This protects against requests that another website triggers in a signed-in browser.

## Ownership

Endpoints that concern a character or a campaign check access on the server:

| Check | Applies to | Answer if it fails |
|---|---|---|
| **Character ownership** | Endpoints with a character key | 400 if the key is missing or invalid, 403 if the character does not belong to the signed-in user |
| **Animal companion ownership** | Endpoints for animal companions | 403 if the companion does not belong to a character of the user |
| **Game master** | Endpoints under `gm/` with a campaign ID | 403 if the user is not the game master of that campaign |
| **Campaign membership** | Campaign documents for players | Access only for members of the campaign |

Ownership is stored by user ID, not by e-mail address (see [ADR 0012](../adr/0012-characters-linked-by-user-id.md)). The game master check is central since the API was consolidated (see [ADR 0010](../adr/0010-consolidating-a-grown-api.md)). Deleting a campaign that belongs to someone else answers 404, the same as an unknown campaign, so the answer does not reveal whether it exists.

The API test suite checks the 401 and 403 cases after every deploy (see [ADR 0008](../adr/0008-api-tests-after-every-deploy.md)).

## Files

Character documents and campaign documents are delivered only through endpoints that apply the checks above. The endpoints for uploading and looking up a character picture check character ownership as well.

## Secrets

- Database credentials and the encryption key are only in the configuration file of each environment on the server.
- Each game master's Anthropic API key is stored encrypted with AES-256-CBC. It is decrypted only for the call to the Anthropic API. The API never returns the key; the app can only ask whether a key is stored.
- Pipeline credentials are GitHub secrets.
- Exception texts from the PDF export go to the server log; the client gets a generic message (ticket 140).

How the web root is protected is described in [ADR 0015](../adr/0015-securing-the-web-root.md).
