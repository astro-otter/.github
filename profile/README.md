# Welcome to OTTER

You have found the GitHub Organization for the Open mulTiwavelength Transient Event Repository (or OTTER)!

Each repo is for a different part of the project tentatively structured as follows:

| Name | Description |
|-----------------------|---------------------------------|
| otter | The Python API for accessing the data in OTTER |
| webotter | Code for development of the frontend website of otter |
| otterdb | Code for managing the backend database of otter |

## Developer Instructions
1. Clone the relevant repos:
   ```
   git clone https://github.com/astro-otter/otter.git
   git clone https://github.com/astro-otter/webotter.git
   git clone https://github.com/astro-otter/otterdb.git
   ```    
2. Build the database. First install arangodb from
   https://www.arangodb.com/download-major/.
   Then, you can build the database by running the
   following commands:
   ```
   cd otterdb/db/
   ./setup.sh
   ```
3. Install otter, the API for this database. From
   the root directory where you installed these repos:
   ```
   cd otter
   python -m pip install -e .
   ```
4. Open the website locally. First you have to navigate
   into the directory hosting the flask info and then
   you can build the website. Run the following commands.
   From the root directory where you installed these repos:
   ```
   cd webotter/
   flask --app webotter run
   ```
