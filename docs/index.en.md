# EDChar

EDChar is a web app for the tabletop role-playing game *Earthdawn*. Players create and manage their characters in it, game masters run their campaigns. The app is a Flutter web app with a PHP backend and is available in English and German.

The app is live at [edchar.schuchi.eu](https://edchar.schuchi.eu).

## What this website shows

EDChar was built with agentic development: several Claude Code instances, each with its own repository and its own rules, work together through a shared ticket board. This website documents both the app and the way it was built.

- **[Showcase](showcase/index.md):** what agentic development looks like in practice, using EDChar as the example. The setup with several instances, the ticket workflow, CLAUDE.md as a working contract, and the rules that grew out of real incidents.
- **[Architecture](architektur/index.md):** how the components of EDChar fit together.
- **[Decisions (ADR)](adr/index.md):** architecture and process decisions with their context and the alternatives that were rejected.
- **[Handbook](handbuch/index.md):** how to use the app, for players and game masters.

!!! note "Still to come"
    Two pages of the showcase are still being written: "Lessons learned" and "Limits and transferability to teams".
