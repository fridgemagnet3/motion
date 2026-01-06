FROM ubuntu:20.04
# core packages

RUN apt-get update && apt-get -y install sudo vim build-essential

# install timezone data otherwise it gets stuck prompting for this info
RUN DEBIAN_FRONTEND=noninteractive TZ=Europe/London apt-get -y install tzdata
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y keyboard-configuration

ENV LANG=en_US.UTF-8
RUN apt-get install --no-install-recommends -y locales && \
    locale-gen ${LANG} && update-locale LANG=${LANG}

RUN apt-get -y install \
autoconf automake autopoint build-essential pkgconf libtool libzip-dev libjpeg-dev git libavformat-dev libavcodec-dev libavutil-dev \
   libswscale-dev libavdevice-dev libwebp-dev gettext libmicrohttpd-dev wget git 

# packaging
RUN apt-get -y install devscripts debhelper

RUN apt-get -y install libpq-dev libsqlite3-dev libmariadbclient-dev

# Add a user account, give sudo access
RUN useradd -m docker && echo "docker:docker" | chpasswd && adduser docker sudo

USER docker
WORKDIR /home/docker
CMD /bin/bash


