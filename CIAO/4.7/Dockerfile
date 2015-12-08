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
	libpython2.7 \
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

COPY .ciaoinstall.rc ciao-install /root/
#COPY ./ciao_download /opt/ciao_download

RUN mkdir -p /opt/ciao_download && bash /root/ciao-install 

# smoke test

CMD bash -c 'source /opt/ciao-4.7/bin/ciao.bash && export LOGNAME=root && cd /opt/ciao-4.7/test && make -k test 2>&1 | tee ~/ciao_test.log'
