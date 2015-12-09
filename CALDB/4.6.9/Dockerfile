# Dockerfile for CALDB
# http://cxc.cfa.harvard.edu/ciao/download/caldb.html

FROM ubuntu:15.10

MAINTAINER ldouchy

# Prerequisite packages installation & clean
RUN apt-get update \
 && apt-get install -y \
	curl \
 && rm -rf /var/lib/apt/lists/*

workdir /opt/CALDB

# caldbmgr:caldb user creation
RUN groupadd caldb && useradd -r -g caldb caldbmgr

# switch to user caldbmgr
USER caldbmgr

# Download 
curl ftp://cda.harvard.edu/pub/arcftp/caldb/caldb_4.6.9_main.tar.gz | tar xz && \
curl ftp://cda.harvard.edu/pub/arcftp/caldb/acis_bkgrnd_4.6.9.tar.gz | tar xz && \
curl ftp://cda.harvard.edu/pub/arcftp/caldb/hrc_bkgrnd_4.6.1.1.tar.gz | tar xz && \
curl ftp://cda.harvard.edu/pub/arcftp/caldb/README_caldb4.6.9.txt > README_caldb4.6.9.txt && \
curl ftp://cda.harvard.edu/pub/arcftp/caldb/MANIFEST_4.6.9_main.txt > MANIFEST_4.6.9_main.txt

