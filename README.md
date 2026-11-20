# EDChar-Docs

**Website: https://tschuchi.github.io/EDChar-Docs/**

EDChar is a web app for the tabletop role-playing game *Earthdawn*: players manage their characters, game masters run their campaigns. It was built by one person, Thore Schuchardt, working with five Claude Code instances – Frontend, Backend, Testing, Board-Keeper and Docs – that coordinate only through a shared ticket board in Git.

This repository contains the public documentation of the app and of the way it was built. It is written by the Docs instance and published with [MkDocs Material](https://squidfunk.github.io/mkdocs-material/) on GitHub Pages.

## What you find on the website

- **[Showcase](https://tschuchi.github.io/EDChar-Docs/showcase/):** what agentic development looks like in practice – the setup with five instances, the ticket workflow, CLAUDE.md as a working contract, the rules and the incidents behind them, facts and figures.
- **[Architecture](https://tschuchi.github.io/EDChar-Docs/architektur/):** how the Flutter web app, the PHP API, the PDF export, the database and the CI/CD pipelines fit together.
- **[Decisions (ADR)](https://tschuchi.github.io/EDChar-Docs/adr/):** architecture and process decisions with their context, the alternatives that were rejected and their consequences.
- **[Handbook](https://tschuchi.github.io/EDChar-Docs/handbuch/):** how to use the app, for players and game masters, in English and German.

## Author

Thore Schuchardt

## Building the site locally

English is the original and default language. German is the translation, selectable via the language switcher. Pages use the suffixes `.en.md` and `.de.md`. A page without a German version falls back to English.

```
pip install -r requirements.txt
mkdocs serve
```

Then open http://127.0.0.1:8000/EDChar-Docs/. To check the build the same way CI does:

```
mkdocs build --strict
```

Work happens on `develop`. The website is built and published by `.github/workflows/pages.yml` on every push to `main`.

---

Earthdawn is a Registered Trademark of FASA Corporation. All Rights Reserved.
