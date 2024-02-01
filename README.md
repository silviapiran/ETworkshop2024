# ETworkshop2024
This repository is dedicated to the hand-on session for the ET workshop 2024,  February 20-23th in Assisi. 


## Prerequisites to run the notebook

If running locally, we suggest using anaconda: https://anaconda.org/

If you are on windows, use the windows subsystem for linux: https://docs.microsoft.com/en-us/windows/wsl/install-win10 plus the ubuntu anaconda.

After installing anaconda, you should (in a terminal):

* clone the repository: git clone git@github.com:FabioRagosta/etworkshop2024.git
* change directories to the repository: cd etworkshop2024

use conda to create an environment:
* on mac osx: conda env create -f environment-osx.yml
* on linux / windows wsl: conda env create -f environment-ubuntu.yml

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

### The data set
Two data files were prepared for this school activity, both in JSON format. JSON files are, essentially, dictionaries.

The alerts were all issued on the night of 2021-02-05 UT. The total number of alerts issued on that night approximated 1 million. If all the alerts were to be used, complete with all their entries, they total disk space for the 2021-02-05 night is larger than 16GB. To facilitate the download and handling of the data, alerts were selected that:
- have at least 2 detections for the source (ndethist >= 2)
- are likely real according to two real/bogus classifiers (drb > 0.8; braai > 0.8)
- left a positive residual after image subtraction, i.e. the flux in the science image is larger than in the template image (warning: the source might have been fainter than the template in a past science image, generating a "negative" subtraction!)

The data files are `data/fast_transient_alerts.json` for the alerts, `data/fast_transient_lc.json` for the light curves.

- `data/fast_transient_alerts.json` Uniform JSON file (readable as a table using `pandas`) containing a selection of relevant information from the original alerts.
- `data/fast_transient_lc.json` Light curves. The light curve of some transients have thousands of data points. To keep the data set manageable and our eyes on the scientific objective to discover fast transients, some the light curves were cut. In particular, **empty light curves** were assigned to those transients that:
    - have at least one "negative" subtraction in the past (see above)
    - are located at Galactic latitude `-8 deg < b < +8 deg` <br>
In addition, only those data points within the last 30 days before the alert was issued are present in the light curves. Long-duration transients, variables, and repeatingly bursting sources are outside the scope of this activity. However, data points acquired after the last alert included in the `fast_transient_alerts.json` file will be present. 

### Useful links
[ZTF Avro schema for the alerts](https://zwickytransientfacility.github.io/ztf-avro-alert/schema.html)<br>
[Public ZTF alerts](https://ztf.uw.edu/alerts/public/)<br>
[Alert brokers for ZTF and Rubin Observatory](https://www.lsst.org/scientists/alert-brokers)
