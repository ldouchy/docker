# BXA over CIAO
# https://johannesbuchner.github.io/BXA

FROM ldouchy/ciao:latest

MAINTAINER ldouchy

LABEL description="BXA https://johannesbuchner.github.io/BXA"

WORKDIR /opt

RUN 	apt-get update && \
	apt-get install -y \
	build-essential \
	cmake \
	git \
	gfortran \
	ipython \
	libatlas3-base libatlas-dev \
	libblas3 libblas-dev \
	libgl1-mesa-dev \
	liblapack3 liblapack-dev \
	python-dev \
	python-matplotlib \
	python-numpy \
	python-progressbar \
	python-scipy \
	python-pyfits \
	feh \
	&& rm -rf /var/lib/apt/lists/*

# Compilation prerequisite variables
ENV CC=/usr/bin/gcc \
    CXX=/usr/bin/g++ \
    FC=/usr/bin/gfortran \
    PYTHON=/usr/bin/python

# Durty trick to avoid "libgfortran.so.3: version `GFORTRAN_1.4' not found"
RUN mv /opt/ciao-4.7/ots/lib/libgfortran.so.3 /opt/ciao-4.7/ots/lib/libgfortran.so.3.bck && ln -s /usr/lib/x86_64-linux-gnu/libgfortran.so.3 /opt/ciao-4.7/ots/lib/libgfortran.so.3

# PyMultiNest install from sources
RUN wget https://raw.githubusercontent.com/ldouchy/docker_PyMultiNest/master/installMultiNest.sh  && /bin/bash /opt/installMultiNest.sh

ENV     LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/MultiNest/lib \
        MULTINEST=$MULTINEST:/opt/MultiNest \
        PYTHONPATH=$PYTHONPATH:/opt/custom/complex_pymultinest/LF_modules/configuration:/opt/custom/complex_pymultinest/LF_modules/models:/opt/BXA

# BXA install from sources
RUN git clone https://github.com/JohannesBuchner/BXA.git && cd /opt/BXA && python setup.py install

# Simple test
WORKDIR /opt/example

COPY reputsimple_pymultinest1d_multimodal_pyinapublicgit.tar.gz /opt/example/
RUN tar -xzvf reputsimple_pymultinest1d_multimodal_pyinapublicgit.tar.gz && rm reputsimple_pymultinest1d_multimodal_pyinapublicgit.tar.gz

CMD sherpa example_simplest.py && feh simplest-plot.png
