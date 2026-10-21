# telbe_ana

Analysis environment for the TELBE 26b TTO RenkuLab project.

## Renku session setup
The files here are only used if the session launcher builds the environment from this repository:
**Sessions → Add session launcher → Create from code**, select this repository, frontend **JupyterLab**.
A launcher with a ready-made image (e.g. "Python Datascience") ignores them.

A built session has two Python environments:
- **`requirements.txt`** goes into the **kernel**, where the notebook code runs. Add analysis packages here (numpy, escape-fel, ...).
- **`jupyterlab_extensions.txt`** goes into the **JupyterLab server**, which draws what you see in the browser.
  Only packages with a JupyterLab part belong here as well (ipympl, widget libraries, voila, ...).

ipympl must be in both files with the same version, and `jupyterlab_widgets` must match `ipywidgets`
(8.1.x ↔ 3.0.x), otherwise `%matplotlib widget` figures appear only as static images.
`jupyterlab_extensions.txt` is read by Renku's JupyterLab buildpack
([source](https://github.com/SwissDataScienceCenter/renku-frontend-buildpacks/blob/main/buildpacks/jupyterlab/bin/build));
this isn't documented. After changing either file, rebuild the environment in Renku.
