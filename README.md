# Template for publishing Julia Jupyter notebooks with dynamic matrix

Click `Use this template` button to copy this repository.

See also:

- [template-juliabook](https://github.com/ww-jl/template-juliabook) : runs notebooks concurrently and [jupyter-book][] builds the website.

[quarto]: https://quarto.org
[jupyter-book]: https://jupyterbook.org
[Literate.jl]: https://github.com/fredrikekre/Literate.jl
[mkdocs-material]: https://squidfunk.github.io/mkdocs-material

## Notebook execution and publish

In [ci.yml](.github/workflows/ci.yml), Jupyter (`*.ipynb`) and Literate (`*.jl`) notebooks under the `docs` folder are executed by GitHub actions; then [Jupyter book][jupyter-book] creates a beautiful website.

### Parallel execution

The notebooks are executed in parallel by dynamic matrix. Every notebook runs on an individual runner.

### Enable GitHub pages

Open your repository settings => Pages => GitHub Pages => Build and deployment => Source, select `GitHub actions`.

## Automatic dependency updates

### Dependabot and Kodiak Bot

See [dependabot.yml](.github/dependabot.yml) configuration.

This repository also uses [Kodiak Bot](https://kodiakhq.com/docs/quickstart) to automatically merge updates. You might need to enable the Kodiak Bot APP.

### Julia dependencies

[update-manifest.yml](.github/workflows/update-manifest.yml) regularly updates Julia dependencies, make a PR with the updated dependencies, and automatically merge the updates if the notebooks are executed smoothly.

See [the instructions](https://github.com/peter-evans/create-pull-request/blob/main/docs/concepts-guidelines.md#triggering-further-workflow-runs) for how to trigger CI workflows in a PR. This repo uses a custom [GitHub APP](https://github.com/peter-evans/create-pull-request/blob/main/docs/concepts-guidelines.md#authenticating-with-github-app-generated-tokens) to generate a token on the fly.

## Checking HTTP links

[linkcheck.yml](.github/workflows/linkcheck.yml) uses GitHub actions to regularly check if the web links in the notebooks are valid.
