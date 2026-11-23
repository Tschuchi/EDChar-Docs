---
hide:
  - navigation
  - toc
---

<div class="edc-hero" markdown>
<h1 class="edc-hero__title">EDChar</h1>

Eine Web-App für das Pen-&-Paper-Rollenspiel *Earthdawn* – und ein Beispiel dafür, was eine Person mit fünf Claude-Code-Instanzen bauen kann, die über ein Ticket-Board zusammenarbeiten.

[Zur App](https://edchar.schuchi.eu){ .md-button }
</div>

EDChar ist eine Web-App für *Earthdawn*. Spieler legen darin ihre Charaktere an und verwalten sie, Spielleiter führen ihre Kampagnen. Die App ist eine Flutter-WebApp mit PHP-Backend, rund 40.800 Zeilen Anwendungscode und rund 17.500 Zeilen Tests ([Stand 2026-11-23](showcase/facts.md#lines-of-code)), und steht auf Englisch und Deutsch zur Verfügung. Diese Website dokumentiert die App und die Art, wie sie gebaut wurde.

<div class="grid cards" markdown>

-   :material-robot-outline:{ .lg .middle } **Showcase**

    ---

    Wie agentische Entwicklung in der Praxis aussieht: das Setup mit fünf Instanzen, der Ticket-Ablauf, CLAUDE.md als Arbeitsvertrag und die Regeln, die aus echten Vorfällen entstanden sind.

    [:octicons-arrow-right-24: Showcase](showcase/index.md)

-   :material-sitemap-outline:{ .lg .middle } **Architektur**

    ---

    Wie Web-App, API, PDF-Export, Datenbank und Pipelines zusammenspielen.

    [:octicons-arrow-right-24: Architektur](architektur/index.md)

-   :material-scale-balance:{ .lg .middle } **Entscheidungen (ADR)**

    ---

    Architektur- und Prozessentscheidungen mit Kontext, verworfenen Alternativen und Folgen.

    [:octicons-arrow-right-24: Entscheidungen](adr/index.md)

-   :material-book-open-variant:{ .lg .middle } **Handbuch**

    ---

    Bedienung der App für Spieler und Spielleiter.

    [:octicons-arrow-right-24: Handbuch](handbuch/index.md)

</div>

!!! note "Noch in Arbeit"
    Zwei Seiten des Showcase entstehen noch: "Lessons learned" und "Limits and transferability to teams". Seiten, die es noch nicht auf Deutsch gibt, erscheinen auf Englisch.
