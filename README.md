# regressiontothemeangirls

Source for the [Regression to the Mean Girls](https://regressiontothemeangirls.com) podcast blog.

## How to add a post

See **[CONTRIBUTING.md](CONTRIBUTING.md)**. Click the button
below, copy `posts/_template/` to a new folder, write your post, run
`quarto render`, and open a pull request.

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/LucyMcGowan/regressiontothemeangirls?quickstart=1)

## How it builds

- Each post is `posts/{slug}/index.qmd` with its images in the same folder.
- Shared post settings are in `posts/_metadata.yml`.
- Code output is cached in `_freeze/`. Contributors render locally / in a Codespace and commit `_freeze/`.
- `.github/workflows/publish.yml` publishes to the `gh-pages` branch on each
  push to `main`; `.github/workflows/preview.yml` renders a build for
  each pull request.
