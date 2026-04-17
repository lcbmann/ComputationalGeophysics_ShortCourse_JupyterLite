# Computational Geophysics Short Course in JupyterLite

This deployment packages the course material as a browser-only JupyterLite site.

## Start here

- [Open JupyterLab](./lab/index.html)
- [Open the JupyterLite smoke test](./lab/index.html?path=00_jupyterlite_smoke_test.ipynb)

## Course content included in this deployment

- `Notebooks/`
- `Slides/`
- `share/images/` placeholder assets used by notebook headers

Inside JupyterLab, browse the `Notebooks` folder to open the course notebooks.

## Important limitations

- This deployment is designed for light, browser-based use. It does not reproduce every feature of a full local Python/Jupyter installation.
- Animation-heavy notebooks may still be slower in the browser than in a local environment.
- Some notebooks originally depended on missing image assets in the source repository. Minimal placeholder assets are included here so those notebooks render cleanly in JupyterLite.

## Recommended quick checks

1. Open `00_jupyterlite_smoke_test.ipynb` and run all cells.
2. Open `Notebooks/02 FiniteDifferenceMethod/01 Derivatives/fd_first_derivative.ipynb` and run all cells.
3. Open one notebook with local helper imports, for example `Notebooks/05 SpectralElements/Wave Equation/se_elastic_1D_homogeneous.ipynb`, and confirm the first helper cell changes into the notebook directory before the imports run.
