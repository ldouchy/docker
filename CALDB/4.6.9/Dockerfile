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
         ftp://cda.harvard.edu/pub/arcftp/caldb/README_caldb4.6.9.txt \
	 ftp://cda.harvard.edu/pub/arcftp/caldb/MANIFEST_4.6.9_main.txt \
# Uncompress
&&  tar xzvf caldb_4.6.9_main.tar.gz \ 

# Clean
&&  rm -f caldb_4.6.9_main.tar.gz

