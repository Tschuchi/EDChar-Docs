---
hide:
  - navigation
  - toc
---

<div class="edc-hero" markdown>
<h1 class="edc-hero__title">EDChar</h1>

A web app for the tabletop role-playing game *Earthdawn* – and an example of what one person can build with five Claude Code instances that work together through a ticket board.

[Open the app](https://edchar.schuchi.eu){ .md-button }
</div>

EDChar is a web app for *Earthdawn*. Players create and manage their characters in it, game masters run their campaigns. The app is a Flutter web app with a PHP backend, about 40,800 lines of application code plus about 17,300 lines of tests ([as of 2026-11-20](showcase/facts.md#lines-of-code)), and is available in English and German. This website documents both the app and the way it was built.

<div class="grid cards" markdown>

-   :material-robot-outline:{ .lg .middle } **Showcase**

    ---

    What agentic development looks like in practice: the setup with five instances, the ticket workflow, CLAUDE.md as a working contract, and the rules that grew out of real incidents.

    [:octicons-arrow-right-24: Showcase](showcase/index.md)

-   :material-sitemap-outline:{ .lg .middle } **Architecture**

    ---

    How the web app, the API, the PDF export, the database and the pipelines fit together.

    [:octicons-arrow-right-24: Architecture](architektur/index.md)

-   :material-scale-balance:{ .lg .middle } **Decisions (ADR)**

    ---

    Architecture and process decisions with their context, the alternatives that were rejected and their consequences.

    [:octicons-arrow-right-24: Decisions](adr/index.md)

-   :material-book-open-variant:{ .lg .middle } **Handbook**

    ---

    How to use the app, for players and game masters.

    [:octicons-arrow-right-24: Handbook](handbuch/index.md)

</div>

!!! note "Still to come"
    Two pages of the showcase are still being written: "Lessons learned" and "Limits and transferability to teams".
