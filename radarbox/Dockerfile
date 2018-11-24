FROM resin/raspberrypi3-debian:stretch

RUN apt-get update && apt-get install -yq --no-install-recommends \
  dirmngr apt-transport-https

ARG KEY_ID=1D043681
RUN apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys ${KEY_ID}

RUN echo 'deb https://apt.rb24.com/ rpi-stable main' >> /etc/apt/sources.list

RUN apt-get update && apt-get install -yq --no-install-recommends \
  rbfeeder && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/*

COPY rbfeeder.ini /etc/

ENTRYPOINT rbfeeder
