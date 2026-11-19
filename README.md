# EDChar-Docs

Public documentation for EDChar, built with [MkDocs Material](https://squidfunk.github.io/mkdocs-material/) and published to GitHub Pages.

English is the original and default language. German is the translation, selectable via the language switcher. Pages use the suffixes `.en.md` and `.de.md`. A page without a German version falls back to English.

## Local preview

```
pip install -r requirements.txt
mkdocs serve
```

Then open http://127.0.0.1:8000. To check the build the same way CI does:

```
mkdocs build --strict
```

## Publishing

Work happens on `develop`. The website is built and published by `.github/workflows/pages.yml` on every push to `main`.
