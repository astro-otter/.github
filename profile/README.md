# Welcome to OTTER

You have found the GitHub Organization for the Open mulTiwavelength Transient Event Repository (or OTTER)!

Each repo is for a different part of the project tentatively structured as follows:

| Name | Description |
|-----------------------|---------------------------------|
| otter | The Python API for accessing the data in OTTER |
| otterdb | Code for managing the backend "database" of otter |
| otter-docker | Code and instructions to use the otter docker image and work with the otter dataset |
| otter-web | Code for development of the frontend website of otter |

## Python API
Once you have the Docker container running you will also have started the API server endpoint. This means
you can also query OTTER from python! See https://astro-otter.readthedocs.io for detailed instructions. A sample
use case to get all of the data for the TDE ASASSN-14li and then access it's coordinates and photometry is below. 
```
# 1) query for the TDE ASASSN-14li 
from otter import Otter
db = Otter()
t = db.query(names="ASASSN-14li")[0]
print(t)

# Get and print an astropy skycoord for ASASSN-14li
coord = t.get_skycoord()
print(coord)

# get the photometry
phot = db.get_phot(names="ASASSN-14li")
print(phot)
```

## Dev Instructions
See the detailed developer installation instructions at: https://astro-otter.readthedocs.io/en/latest/introduction.html#developer-installation
