# HiverseBook

This repository contains a Quarto book for onboarding new Isazi employees to
the Hudson package ecosystem.

## Render locally

You need Quarto installed and available on your `PATH`.

From the repository root:

```bash
quarto render
```

To render PDF instead:

```bash
quarto render --to pdf
```

To render both configured formats:

```bash
quarto render --to html --to pdf
```

The rendered site is written into `docs/`, which is what GitHub Pages serves in
this repository setup.

## Publish on GitHub Pages

1. Install Quarto and confirm `quarto check install` succeeds.
2. Render the book:
   ```bash
   quarto render
   ```
3. Commit both the source files and the rendered `docs/` folder:
   ```bash
   git add .
   git commit -m "Render book"
   git push
   ```
4. In GitHub, set `Settings -> Pages -> Source` to `GitHub Actions`.
5. The included workflow in `.github/workflows/deploy.yml` will deploy the
   contents of `docs/` to GitHub Pages on every push to `main`.

## Notes

- Many package-specific chunks are marked `eval: false` because they require
  installed Hudson packages, database access, or API keys.
- Some visual chunks use only base R and should render without special setup.
- PDF rendering also needs a LaTeX installation such as TinyTeX.
