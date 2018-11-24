FROM resin/raspberrypi3-debian:stretch

RUN apt-get update && apt-get install -yq --no-install-recommends wget

WORKDIR /usr/src

RUN wget http://flightaware.com/adsb/piaware/files/packages/pool/piaware/p/piaware-support/piaware-repository_3.6.3_all.deb
RUN dpkg -i piaware-repository_3.6.3_all.deb

RUN apt-get update && apt-get install -yq --no-install-recommends \
  supervisor \
  dump1090-fa && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/*

RUN mkdir /tmp/dump1090
RUN sed -i 's|/run/dump1090-fa/|/tmp/dump1090/|g' /etc/lighttpd/conf-available/89-dump1090-fa.conf

ADD supervisor /etc/supervisor

EXPOSE 8080 30001 30002 30003 30004 30005

ENTRYPOINT supervisord -c /etc/supervisor/supervisord.conf
