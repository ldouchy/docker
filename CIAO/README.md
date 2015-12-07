# [CIAO](http://cxc.harvard.edu/ciao/index.html) docker image

## Acknowledgement

If you are writing a paper and would like to cite the CIAO software, we recommend the following:

CIAO: Chandra's data analysis system ([ADS](http://adsabs.harvard.edu/abs/2006SPIE.6270E..60F), [PS](http://cxc.harvard.edu/ciao/download/papers/spie_cite.ps))
Fruscione et al. 2006, SPIE Proc. 6270, 62701V, D.R. Silvia & R.E. Doxsey, eds.


The specific version of CIAO and CALDB used for the analysis should be mentioned. Further guidelines are available from the [Acknowledgment of Use of Chandra Resources](http://cxc.harvard.edu/cda/acknowledgment.html). 

## Default beaviour of the container:
Launched without option this container will run the full CIAO smoke test. Specific option are needed:

/!\ you need to authorize the container to access your local X server. /!\

On linux:

	$ docker run -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=$DISPLAY ldouchy/ciao:latest

# CIAO links

[CIAO main page](http://cxc.harvard.edu/ciao/index.html)

[Bugs: Installation & Smoke Tests](http://cxc.harvard.edu/ciao/bugs/smoke.html)

CIAO FTP: ftp://cxc.harvard.edu/pub/
