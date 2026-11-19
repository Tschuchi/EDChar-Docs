# Decisions (ADR)

Architecture Decision Records: one page per decision, with context, decision, rejected alternatives, consequences and sources. The sources are ticket numbers on the project's ticket board and commits of the CLAUDE.md files.

Where the board does not record alternatives or reasons, the ADR says so instead of filling the gap.

## Organisation and process

| ADR | Decision |
|---|---|
| [0001](0001-multiple-agent-instances.md) | Several Claude Code instances with separate repositories |
| [0002](0002-control-model.md) | Control model: the human owns decisions and the start signal, agents own execution |
| [0003](0003-markdown-board-in-git.md) | Own Markdown board in Git instead of GitHub Issues or Jira |
| [0004](0004-ticket-lifecycle.md) | Ticket lifecycle with a "Next" field and a testing gate |
| [0005](0005-observed-or-derived.md) | Label every finding as "observed" or "derived from the code" |
| [0006](0006-golive.md) | GoLive: the instances merge themselves, backend first |
| [0007](0007-one-version-per-golive.md) | One version number per GoLive, plus a build ID |

## Testing

| ADR | Decision |
|---|---|
| [0008](0008-api-tests-after-every-deploy.md) | Automated API tests after every deploy to the build server |
| [0009](0009-ui-tests-with-playwright.md) | UI tests with Playwright and dedicated test accounts |

## API, data and security

| ADR | Decision |
|---|---|
| [0010](0010-consolidating-a-grown-api.md) | Consolidating a grown API |
| [0011](0011-charkey-at-the-interface.md) | `charKey` as the standard name at the interface, database columns unchanged |
| [0012](0012-characters-linked-by-user-id.md) | Characters are linked to their owner by user ID, not by e-mail address |
| [0013](0013-character-documents-as-markdown-files.md) | Character documents as Markdown files instead of database records |
| [0014](0014-own-markdown-editor.md) | Own Markdown editor instead of an editor library |
| [0015](0015-securing-the-web-root.md) | Securing the web root |
