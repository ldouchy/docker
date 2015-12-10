# Dockerfile add Background files to CALDB
# http://cxc.cfa.harvard.edu/ciao/download/caldb.html

FROM ldouchy/caldb:4.6.9

MAINTAINER ldouchy

# Prerequisite packages installation & clean

# switch to user caldbmgr
USER caldbmgr

workdir /opt/CALDB

#COPY ./caldb_download/* /opt/CALDB/

# Download 
RUN wget ftp://cda.harvard.edu/pub/arcftp/caldb/acis_bkgrnd_4.6.9.tar.gz \
	 ftp://cda.harvard.edu/pub/arcftp/caldb/hrc_bkgrnd_4.6.1.1.tar.gz \
# Uncompress
&&  tar xzvf acis_bkgrnd_4.6.9.tar.gz \
	     hrc_bkgrnd_4.6.1.1.tar.gz \
# Clean
&&  rm -f *.tar.gz

