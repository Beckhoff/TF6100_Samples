FROM debian:trixie-slim

# Install curl and ca-certificates to load bhf.asc signing file from beckhoff.com during build
RUN apt-get update \
    && apt-get install --yes --no-install-recommends \
    curl \
    ca-certificates \
    iputils-ping

# Use login information in the bhf.conf file to authenticate against deb*.beckhoff.com
# See https://manpages.debian.org/testing/apt/apt_auth.conf.5.en.html for more information
RUN --mount=type=secret,id=apt \
    curl --fail --netrc-file "/run/secrets/apt" \
    -o /usr/share/keyrings/bhf.asc \
    https://deb.beckhoff.com/repo.pub

# Replace default debian.org package sources.
# From here on, all packages will be loaded from deb*.beckhoff.com
RUN rm /etc/apt/sources.list.d/debian.sources
COPY ./apt-config/bhf.list ./apt-config/debian.sources.list /etc/apt/sources.list.d/

# Install TwinCAT runtime package
RUN --mount=type=secret,id=apt \
     apt-get -o "Dir::Etc::netrc=/run/secrets/apt" update \
     && apt-get -o "Dir::Etc::netrc=/run/secrets/apt" install --yes \
     tc31-xar-um \
     tf610x-opcuaclientpubsub-xar \
     && rm -rf /var/lib/apt/lists/*

# Install TwinCAT runtime package
#COPY ./tf610x-opcuaclientpubsub-xar.deb /files/tf610x-opcuaclientpubsub-xar.deb
#RUN dpkg -i /files/tf610x-opcuaclientpubsub-xar.deb

# As an example, copy basic TwinCAT runtime configurations files
ARG TC3_DIR=/etc/TwinCAT/3.1
COPY TwinCAT/StaticRoutes.xml $TC3_DIR/Target/
COPY TwinCAT/SysStartupState.reg $TC3_DIR/Target/RegFiles/

EXPOSE 8016/tcp
EXPOSE 48898/tcp
EXPOSE 48899/udp

WORKDIR /app
COPY entrypoint.sh /app/

CMD [ "/bin/sh", "/app/entrypoint.sh"]
