# Dockerfile for CIAO recommended install 
# http://cxc.harvard.edu/ciao/

FROM ubuntu:15.10

MAINTAINER ldouchy

# Prerequisite packages installation & clean
RUN apt-get update \
 && apt-get install -y \
	libfontconfig1 \
	libglu1-mesa \
	libgl1-mesa-dev \
	libxcb-shm0 \
	libxcomposite1 \
	libxcursor1 \
	libxft2 \
	libxinerama1 \
	libxml2 \
	libxrandr2 \
	libxss1 \
	libxt6 \
	make \
	wget \
 && rm -rf /var/lib/apt/lists/*

# Dockerfile prerequisite variables
ENV VERSION=4.7

LABEL CIAO_version="$VERSION" description="CIAO software http://cxc.harvard.edu/ciao/"

WORKDIR /opt

#COPY ./ciao_download/ /opt/ciao_download/
COPY .ciaoinstall.rc /root/

RUN mkdir /opt/ciao_download && wget ftp://cxc.harvard.edu/pub/ciao4.7/all/ciao-install && bash ciao-install && rm -rf /opt/ciao_download

ENV AHELP_DEFCONTEXT=/py[.]*/ \
    ASCDS_BIN=/opt/ciao-4.7/bin \
    ASCDS_CALIB=/opt/ciao-4.7/data \
    ASCDS_CONTRIB=/opt/ciao-4.7/contrib \
    ASCDS_IMAGER_PATH=/opt/ciao-4.7/ots/bin \
    ASCDS_INSTALL=/opt/ciao-4.7 \
    ASCDS_LIB=/opt/ciao-4.7/lib \
    ASCDS_PROP_DATE_DATA=/opt/ciao-4.7/config/jcm_data \
    ASCDS_PROP_NHBASE=/opt/ciao-4.7/config/jcm_data \
    ASCDS_PROP_PREC_DATA=/opt/ciao-4.7/config/jcm_dat \
    ASCDS_TMP=/tmp \
    ASCDS_WORK_PATH=/tmp \
    CHIPS_GS_LIB=/opt/ciao-4.7/ots/share/ghostscript/8.56/lib/ \
    CHIPS_OS_LIBS= \
    CIAO_APP_IPYTHON=CIAO \
    CIAO_APP_PYTHON=CIAO \
    CIAO_HEADAS=/opt/ciao-4.7/ots/spectral \
    CIAO_IPYTHON=CIAO \
    CIAO_PYTHON=CIAO \
    CIAO_PYTHON_EXE=/opt/ciao-4.7/ots/bin/python \
    CIAO_PYTHON_PATH=prepend \
    CIAO_SCRIPT_LANG=python \
    CIAO_XPA=CIAO \
    DATA_ROOT=/opt/ciao-4.7/config \
    HEADAS=/opt/ciao-4.7/ots/spectral \
    IPYTHONDIR=/root/.ipython-ciao4.5 \
    JCMLIBDATA=/opt/ciao-4.7/config/jcm_data \
    JCMPATH=/opt/ciao-4.7/config/jcm_data \
    LD_LIBRARY_PATH=/opt/ciao-4.7/lib:/opt/ciao-4.7/ots/lib:/opt/ciao-4.7/contrib/lib \
    OBSVIS_PKG_PATH=/opt/ciao-4.7/lib/tcltk/packages/obsvis \
    PANGO_RC_FILE=/opt/ciao-4.7/ots/etc/pango/pangorc \
    PATH=$PATH:/opt/ciao-4.7/bin:/opt/ciao-4.7/ots/bin:/opt/ciao-4.7/contrib/bin \
    PFILES=/root/cxcds_param4:;/opt/ciao-4.7/contrib/param:/opt/ciao-4.7/param \
    PYTHON=/usr/bin/python \
    PYTHONPATH=/opt/ciao-4.7/lib/python2.7/site-packages:/opt/ciao-4.7/ots/lib/python2.7/site-packages:/opt/ciao-4.7/contrib/lib/python2.7/site-packages \
    SHLVL=1 \
    XPA_METHOD=local \
    XSPEC_HELP_FILE=/opt/ciao-4.7/doc/xspec.hlp

# smoke test
CMD cd $ASCDS_INSTALL/test && make -k test 2>&1 | tee ~/ciao_test.log
