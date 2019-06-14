FROM dataiku/dss
MAINTAINER Carl Wallace Handlin <cwallaceh@gmail.com>

USER root

# Install Python3.x.x
RUN apt-get update
RUN apt-get -y upgrade
RUN apt-get install -y python3-pip
RUN apt-get install -y build-essential libssl-dev libffi-dev python-dev

# Install geospatial dependencies
RUN apt-get install -y libspatialindex-dev

# Install R
RUN apt-get install -y r-base r-base-dev

USER dataiku