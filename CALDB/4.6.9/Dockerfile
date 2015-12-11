# Dockerfile for CALDB
# http://cxc.cfa.harvard.edu/ciao/download/caldb.html

FROM ubuntu:15.10

MAINTAINER ldouchy

# Prerequisite packages installation & clean
RUN apt-get update \
 && apt-get install -y \
	wget \
 && rm -rf /var/lib/apt/lists/*

# caldbmgr:caldb user creation
RUN mkdir /opt/CALDB && groupadd caldb && useradd -r -g caldb caldbmgr && chown caldbmgr:caldb /opt/CALDB

# switch to user caldbmgr
USER caldbmgr

workdir /opt/CALDB

#COPY ./caldb_download/* /opt/CALDB/

# Download 
RUN wget ftp://cda.harvard.edu/pub/arcftp/caldb/caldb_4.6.9_main.tar.gz \
&&  tar xzvf caldb_4.6.9_main.tar.gz \
&&  rm -f caldb_4.6.9_main.tar.gz
RUN  wget ftp://cda.harvard.edu/pub/arcftp/caldb/acis_bkgrnd_4.6.9.tar.gz \
&&  tar xzvf acis_bkgrnd_4.6.9.tar.gz \
&&  rm -f acis_bkgrnd_4.6.9.tar.gz
RUN  wget ftp://cda.harvard.edu/pub/arcftp/caldb/hrc_bkgrnd_4.6.1.1.tar.gz \
&&  tar xzvf hrc_bkgrnd_4.6.1.1.tar.gz \
&&  rm -f hrc_bkgrnd_4.6.1.1.tar.gz

#&&  wget ftp://cda.harvard.edu/pub/arcftp/caldb/README_caldb4.6.9.txt \
#&&  wget ftp://cda.harvard.edu/pub/arcftp/caldb/MANIFEST_4.6.9_main.txt \

