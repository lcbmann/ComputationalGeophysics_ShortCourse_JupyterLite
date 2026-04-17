# JupyterLite

This repository includes a JupyterLite version of the course.

It is a browser-based copy of the material, built for GitHub Pages.

The main idea is simple:

- the course notebooks are included in the JupyterLite site
- the slides are included as static files
- the site is deployed with GitHub Actions

The Lite build uses `xeus-python` with a small scientific Python stack, mainly `numpy` and `matplotlib`.

This is meant as a lightweight way to browse and run parts of the course in the browser. It is not a full replacement for a normal local Python/Jupyter setup.

Some notes:

- simple notebooks should work well
- heavier animation notebooks may still be slower in the browser
- some notebook paths and assets were adjusted so the material can open more cleanly in JupyterLite

In short, this is a browser-friendly version of the course, useful for testing, teaching, and light interactive use.
