FROM resin/raspberrypi3-debian:stretch

ARG KEY_ID=40C430F5
RUN apt-key adv --recv-key --keyserver pool.sks-keyservers.net ${KEY_ID} || \
     apt-key adv --recv-key --keyserver pgp.mit.edu ${KEY_ID}

RUN echo 'deb http://repo.feed.flightradar24.com flightradar24 raspberrypi-stable' >> /etc/apt/sources.list

RUN apt-get update && apt-get install -yq --no-install-recommends \
  dirmngr && \
  apt-get install -o Dpkg::Options::="--force-confdef" -o Dpkg::Options::="--force-confold" -y fr24feed && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/*

COPY fr24feed.ini /etc/

ENTRYPOINT fr24feed
