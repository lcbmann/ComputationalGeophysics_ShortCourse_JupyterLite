# JupyterLite Pilot

This repository now includes a JupyterLite deployment path so the course can be tested in a fully browser-based setup without Binder or a dedicated notebook server.

## What is included

- A GitHub Pages workflow at `.github/workflows/deploy.yml`
- A dedicated JupyterLite build environment at `.github/build-environment.yml`
- A dedicated xeus-python runtime environment at `environment-jupyterlite.yml`
- A browser-safe starter notebook in `content/00_jupyterlite_smoke_test.ipynb`
- The full `Notebooks/` tree packaged into the Lite build
- The `Slides/` directory packaged into the Lite build
- A `share/images/` directory with placeholder assets for notebook headers

## Why this starts small

Professor Igel's suggestion was the right one: start with one notebook that has almost no dependencies, confirm the build and execution model, then add real course notebooks incrementally.

The current deployment now does both:

- a very small smoke-test notebook for sanity checking
- the full course notebook tree for exploratory browser-based use

The starter notebook uses only:

- `xeus-python`
- `numpy`
- `matplotlib`

That keeps the first deployment close to "hello world", while still matching the numerical flavor of the course.

## How to enable the deployment

1. Push the repository changes to the `main` branch.
2. In GitHub, open `Settings > Pages`.
3. Set the source to `GitHub Actions`.
4. In `Settings > Actions > General`, make sure workflows are allowed. If deployment fails, also verify the workflow has permission to write pages artifacts.
5. Wait for the `Build and Deploy JupyterLite` workflow to finish.

The site should then appear at:

`https://heinerigel.github.io/ComputationalGeophysics_ShortCourse/`

The JupyterLab app is at:

`https://heinerigel.github.io/ComputationalGeophysics_ShortCourse/lab/index.html`

Inside the site, first open:

`00_jupyterlite_smoke_test.ipynb`

## Current packaging strategy

The full repo is now packaged into the Lite site with these additions:

- all notebooks copied into the site
- helper Python files copied alongside their notebooks
- stale notebook outputs stripped to reduce legacy browser-specific JS and site size
- JupyterLite helper cells inserted into notebooks that import adjacent local modules
- placeholder image assets added where the repository referenced files that did not exist

## Recommended first real notebook to test

The cleanest browser test from the existing course material remains:

`Notebooks/02 FiniteDifferenceMethod/01 Derivatives/fd_first_derivative.ipynb`

Reasons:

- it depends only on `numpy` and `matplotlib`
- it is directly relevant to the course
- it is much lighter than the animation-heavy notebooks

## Main blockers found in the current notebook set

- Some notebooks generate large HTML/JS animations, which remain heavier in the browser than in a local Jupyter setup.
- Numerical notebooks with local helper imports are now packaged for Lite, but should still be tested individually because the original repo was not written for browser-only execution.

## Practical migration order

1. Confirm the smoke-test notebook runs on GitHub Pages.
2. Run `fd_first_derivative.ipynb`.
3. Run one notebook with local helper imports.
4. Only after that, attempt the largest animation-heavy notebooks.

This keeps the risk low and makes it obvious where JupyterLite is already sufficient and where the notebooks still need cleanup.
