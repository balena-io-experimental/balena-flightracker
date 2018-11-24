FROM resin/raspberrypi3-debian:stretch

RUN apt-get update && apt-get install -yq --no-install-recommends wget

WORKDIR /usr/src
RUN wget http://flightaware.com/adsb/piaware/files/packages/pool/piaware/p/piaware-support/piaware-repository_3.6.3_all.deb
RUN dpkg -i piaware-repository_3.6.3_all.deb

RUN apt-get update && apt-get install -yq --no-install-recommends \
  piaware && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/*

COPY piaware.conf /etc/

ENTRYPOINT piaware
