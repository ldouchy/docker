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
ENV VERSION=4.7 \
    ROOT_INSTALL=/opt/ciao-4.7

LABEL CIAO_version="$VERSION" description="CIAO software http://cxc.harvard.edu/ciao/"

WORKDIR /opt

#COPY ./ciao_download/ /opt/ciao_download/
COPY .ciaoinstall.rc /root/

RUN mkdir /opt/ciao_download && wget ftp://cxc.harvard.edu/pub/ciao4.7/all/ciao-install && bash ciao-install && rm -rf /opt/ciao_download

ENV AHELP_DEFCONTEXT=/py[.]*/ \
    ASCDS_BIN=${ROOT_INSTALL}/bin \
    ASCDS_CALIB=${ROOT_INSTALL}/data \
    ASCDS_CONTRIB=${ROOT_INSTALL}/contrib \
    ASCDS_IMAGER_PATH=${ROOT_INSTALL}/ots/bin \
    ASCDS_INSTALL=${ROOT_INSTALL} \
    ASCDS_LIB=${ROOT_INSTALL}/lib \
    ASCDS_PROP_DATE_DATA=${ROOT_INSTALL}/config/jcm_data \
    ASCDS_PROP_NHBASE=${ROOT_INSTALL}/config/jcm_data \
    ASCDS_PROP_PREC_DATA=${ROOT_INSTALL}/config/jcm_dat \
    ASCDS_TMP=/tmp \
    ASCDS_WORK_PATH=/tmp \
    CHIPS_GS_LIB=${ROOT_INSTALL}/ots/share/ghostscript/8.56/lib/ \
    CHIPS_OS_LIBS= \
    CIAO_APP_IPYTHON=CIAO \
    CIAO_APP_PYTHON=CIAO \
    CIAO_HEADAS=${ROOT_INSTALL}/ots/spectral \
    CIAO_IPYTHON=CIAO \
    CIAO_PYTHON=CIAO \
    CIAO_PYTHON_EXE=${ROOT_INSTALL}/ots/bin/python \
    CIAO_PYTHON_PATH=prepend \
    CIAO_SCRIPT_LANG=python \
    CIAO_XPA=CIAO \
    DATA_ROOT=${ROOT_INSTALL}/config \
    HEADAS=${ROOT_INSTALL}/ots/spectral \
    IPYTHONDIR=/root/.ipython-ciao4.5 \
    JCMLIBDATA=${ROOT_INSTALL}/config/jcm_data \
    JCMPATH=${ROOT_INSTALL}/config/jcm_data \
    LD_LIBRARY_PATH=${ROOT_INSTALL}/lib:${ROOT_INSTALL}/ots/lib:${ROOT_INSTALL}/contrib/lib \
    OBSVIS_PKG_PATH=${ROOT_INSTALL}/lib/tcltk/packages/obsvis \
    PANGO_RC_FILE=${ROOT_INSTALL}/ots/etc/pango/pangorc \
    PATH=$PATH:${ROOT_INSTALL}/bin:${ROOT_INSTALL}/ots/bin:${ROOT_INSTALL}/contrib/bin \
    PFILES=/root/cxcds_param4:${ROOT_INSTALL}/contrib/param:${ROOT_INSTALL}/param \
    PYTHON=/usr/bin/python \
    PYTHONPATH=${ROOT_INSTALL}/lib/python2.7/site-packages:${ROOT_INSTALL}/ots/lib/python2.7/site-packages:${ROOT_INSTALL}/contrib/lib/python2.7/site-packages \
    SHLVL=1 \
    XPA_METHOD=local \
    XSPEC_HELP_FILE=${ROOT_INSTALL}/doc/xspec.hlp

# smoke test
CMD cd $ASCDS_INSTALL/test && make -k test 2>&1 | tee ~/ciao_test.log
