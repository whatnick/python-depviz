# Python Dependency Tree Visualizer

This project visualizes the dependency tree for Python environments. This is a hobby project born out of the frustration with
managing complex Python environments reliably and continuously adding packages to them. It is meant to help isolate unrelated
packages or identify critical packages upgrading which will have very wide ranging impact. It also does not address issues with
ABI's(usually pronounced Abyss), that will need a new tool which tracks python dependencies back to C/C++/Fortran and other
system language land.

See a sample [here](https://whatnick.github.io/python-depviz/index.html).

A much simpler bare osgeo4w python environment for comparison is [here](https://whatnick.github.io/python-depviz/osgeo4w.html).

Geoscience Australia [DEA Sandbox](https://app.sandbox.dea.ga.gov.au/) is included as a sample environment. The following steps were performed to build the sample.

- Pull [sandbox docker image](https://hub.docker.com/r/geoscienceaustralia/sandbox/tags?page=1&ordering=last_updated) or log onto sandbox
- Install pipdeptree with `pip install pipdeptree` at the console or via a notebook.
- Generate and persist dependency graph via `pipdeptree -j > dependencies.json`
- Load graph data onto [3d-force-graph](https://github.com/vasturiano/3d-force-graph) using js object version of the JSON or via fetch API when the file is hosted on https.
- Display app in web page after reorganizing the tree into nodes and edges format the library accepts.
- For a live deployment run sandbox container for Jhub based development
  - Dynamically install packages in the hub
  - Persist graph regularly via pipdeptree
  - Push to viz and update page