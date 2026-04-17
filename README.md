# ComputationalGeophysics_ShortCourse

### Short Course on *Computational Methods in Geophysics*

This repository contains the material for the short course on computational methods in geophysics.

It includes:

- course notebooks
- slides
- a local Conda environment file
- a JupyterLite version of the course for browser-based use

The notebooks were originally written for normal Jupyter/Python use, but this fork also packages them into JupyterLite so they can be opened in the browser without Binder.

Other ways to access related material:

- [Binder](https://mybinder.org/v2/gh/heinerigel/ComputationalGeophysics_ShortCourse/HEAD?urlpath=/tree/)
- [Seismo-live](https://seismo-live.github.io)
- [Coursera](https://www.coursera.org/learn/computers-waves-simulations)

The JupyterLite-specific notes are in `JUPYTERLITE.md`.

For local use, create the environment from `environment.yml`:

> conda env create -f environment.yml

Then activate it:

> conda activate shortcourse
