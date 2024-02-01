# ETworkshop2024
This repository is dedicated to the hand-on session for the ET workshop 2024,  February 20-23th in Assisi. 


## Prerequisites to run the notebook

If running locally, we suggest using anaconda: https://anaconda.org/

If you are on windows, use the windows subsystem for linux: https://docs.microsoft.com/en-us/windows/wsl/install-win10 plus the ubuntu anaconda.

After installing anaconda, you should (in a terminal):

* clone the repository: git clone git@github.com:FabioRagosta/etworkshop2024.git
* change directories to the repository: cd etworkshop2024

use conda to create an environment:
conda env create -f environment.yml

Activate the environment with:

* conda activate etworkshop2024

(if you are running an older version of conda you may need):<br>
source activate etworkshop2024 and can test by opening the first lecture:

* cd etworkshop2024
* upyter notebook GW_followup.ipynb


Will need to create an IRSA account for data access: https://irsa.ipac.caltech.edu/frontpage/

### Objectives

- Learn how to ise LIGO/VIRGO localizations and cross-match with galaxies
- Learn how to build a light curve using Alerts stream
- Learn how classification tools work

## Key steps
- Manipulate HEALPix localization files
- Cross-match a LIGO localization with a galaxy catalog
- read and understand the data
- plot light curves
- apply cuts progressively
- when < 10 candidates are left, inspect them in detail

## Required dependencies

The following required dependencies should be obtainable via the Google Colab, but should also be installable to your local environment using `pip install <module>` and `conda install <module>`.

### Python modules
* python 3
* astropy
* numpy
* pandas
* scipy
* matplotlib
* healpy
* ligo.skymap
* collection

### External packages
None

### Useful links
[ZTF Avro schema for the alerts](https://zwickytransientfacility.github.io/ztf-avro-alert/schema.html)<br>
[Public ZTF alerts](https://ztf.uw.edu/alerts/public/)<br>
[Alert brokers for ZTF and Rubin Observatory](https://www.lsst.org/scientists/alert-brokers)
