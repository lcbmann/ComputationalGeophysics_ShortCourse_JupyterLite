# JupyterLite Pilot

This repository now includes a minimal JupyterLite pilot so the course can be tested in a fully browser-based setup without Binder or a dedicated notebook server.

## What is included

- A GitHub Pages workflow at `.github/workflows/deploy.yml`
- A dedicated JupyterLite build environment at `.github/build-environment.yml`
- A dedicated xeus-python runtime environment at `environment-jupyterlite.yml`
- One very small browser-safe starter notebook in `content/00_jupyterlite_smoke_test.ipynb`

## Why this starts small

Professor Igel's suggestion was the right one: start with one notebook that has almost no dependencies, confirm the build and execution model, then add real course notebooks incrementally.

The current starter notebook uses only:

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

Inside the site, open:

`00_jupyterlite_smoke_test.ipynb`

## Recommended next notebook to port

The cleanest next candidate from the existing course material is:

`Notebooks/02 FiniteDifferenceMethod/01 Derivatives/fd_first_derivative.ipynb`

Reasons:

- it appears to depend only on `numpy` and `matplotlib`
- it is directly relevant to the course
- it is much lighter than the animation-heavy notebooks

## Main blockers found in the current notebook set

- Many notebooks reference banner assets such as `title01.png` or `../../share/images/...`, but those image files are not present in this repository.
- Several notebooks rely on adjacent helper modules such as `animation.py`, `progress_bar.py`, `ricker.py`, `gll.py`, and related local imports.
- Some notebooks generate animations, which need separate browser testing in JupyterLite.

## Practical migration order

1. Confirm the smoke-test notebook runs on GitHub Pages.
2. Port `fd_first_derivative.ipynb` into `content/` after removing or replacing the missing title image.
3. Test local imports with one notebook that uses a nearby helper module.
4. Only after that, attempt the animation-heavy notebooks.

This keeps the risk low and makes it obvious where JupyterLite is already sufficient and where the notebooks still need cleanup.
