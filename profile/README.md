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

## Citing OTTER
If you make use of OTTER in your research please cite both our catalog and software papers:
```
@ARTICLE{Franz2025_OTTER_Catalog,
       author = {{Franz}, Noah and {Alexander}, Kate D and {Gomez}, Sebastian and {Christy}, Collin T and {Laskar}, Tanmoy and {van Velzen}, Sjoert and {Earl}, Nicholas and {Gezari}, Suvi and {Karmen}, Mitchell and {Margutti}, Raffaella and {Pearson}, Jeniveve and {Villar}, V. Ashley and {Zabludoff}, Ann I},
        title = "{The Open mulTiwavelength Transient Event Repository (OTTER): Infrastructure Release and Tidal Disruption Event Catalog}",
      journal = {arXiv e-prints},
     keywords = {High Energy Astrophysical Phenomena, Instrumentation and Methods for Astrophysics},
         year = 2025,
        month = sep,
          eid = {arXiv:2509.05405},
        pages = {arXiv:2509.05405},
archivePrefix = {arXiv},
       eprint = {2509.05405},
 primaryClass = {astro-ph.HE},
       adsurl = {https://ui.adsabs.harvard.edu/abs/2025arXiv250905405F},
      adsnote = {Provided by the SAO/NASA Astrophysics Data System}
}

@article{Franz2026_OTTER_API,
  doi = {10.21105/joss.09516},
  url = {https://doi.org/10.21105/joss.09516},
  year = {2026},
  publisher = {The Open Journal},
  volume = {11},
  number = {118},
  pages = {9516},
  author = {Franz, Noah and Alexander, Kate D. and Gomez, Sebastian},
  title = {A Python API for OTTER},
  journal = {Journal of Open Source Software}
} 
```

## Dev Instructions
See the detailed developer installation instructions at: https://astro-otter.readthedocs.io/en/latest/introduction.html#developer-installation
