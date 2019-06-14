FROM centos:centos7
MAINTAINER Carl Wallace Handlin <cwallaceh@gmail.com>

ENV DSS_VERSION="5.1.4" \
    DSS_DATADIR="/home/dataiku/dss" \
    DSS_PORT=10000

# Dataiku account and data dir setup
RUN useradd -s /bin/bash dataiku \
    && mkdir -p /home/dataiku ${DSS_DATADIR} \
    && chown -Rh dataiku:dataiku /home/dataiku ${DSS_DATADIR}

# Download and extract DSS kit
RUN DSSKIT="dataiku-dss-$DSS_VERSION" \
    && cd /home/dataiku \
    && echo "+ Downloading kit" \
    && curl -OsS "https://downloads.dataiku.com/public/studio/$DSS_VERSION/$DSSKIT.tar.gz" \
    && echo "+ Extracting kit" \
    && tar xf "$DSSKIT.tar.gz" \
    && rm "$DSSKIT.tar.gz" \
    && echo "+ Compiling Python code" \
    && python2.7 -m compileall -q "$DSSKIT"/python "$DSSKIT"/dku-jupyter \
    && { python2.7 -m compileall -q "$DSSKIT"/python.packages >/dev/null || true; } \
    && chown -Rh dataiku:dataiku "$DSSKIT"

# Install depedencies
RUN /home/dataiku/dataiku-dss-$DSS_VERSION/scripts/install/install-deps.sh -yes

# Entry point
WORKDIR /home/dataiku
COPY run.sh /home/dataiku/
RUN chmod +x /home/dataiku/run.sh
USER dataiku

EXPOSE $DSS_PORT

CMD [ "/home/dataiku/run.sh" ]