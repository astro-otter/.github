# Welcome to OTTER

You have found the GitHub Organization for the Open mulTiwavelength Transient Event Repository (or OTTER)!

Each repo is for a different part of the project tentatively structured as follows:

| Name | Description |
|-----------------------|---------------------------------|
| otter | The Python API for accessing the data in OTTER |
| otterdb | Code for managing the backend "database" of otter |
| otter-docker | Code and instructions to use the otter docker image and work with the otter dataset |
| webotter | Code for development of the frontend website of otter (currently deprecated) |

## OTTER Docker Instructions
Install docker, clone the `otter-docker` repo, and then run `./build.sh`. Then you will have a standalone
jupyter lab server at `localhost:8989` for you to work with the otter dataset in! That's it!

See the README file in the `otter-docker` repo for more detailed instructions

## Developer Instructions
1. Set the `OTTER_ROOT` environment variable
   ```
   export OTTER_ROOT=/path/to/where/to/clone
   ```
2. Clone the relevant repos:
   ```
   git clone https://github.com/astro-otter/otter.git $OTTER_ROOT/otter
   git clone https://github.com/astro-otter/otterdb.git $OTTER_ROOT/otterdb
   ```
3. Install the NASA ADS Python API by following the instructions at https://ads.readthedocs.io/en/latest/#getting-started
4. Install otter, the API for this database. From
   the root directory where you installed these repos:
   ```
   cd $OTTER_ROOT/otter
   python -m pip install -e .
   ```
5. Process the data to build the local "database" (although it is really just a directory).
   Then, you can build the "database" by running the
   following commands:
   ```
   cd $OTTER_ROOT/otter/scripts/
   python3 gen_summary_table.py --otterroot $OTTER_ROOT
   ```
6. Easily access the data using the Otter code! In python:
  ```
  import os
  from otter import Otter
  otter = Otter(os.path.join(os.environ['OTTER_ROOT'], 'otterdb', '.otter'))
  res = otter.query(names='AT2018hyz')
  print(res)
  ```
