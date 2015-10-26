FROM armv7/armhf-ubuntu:latest

RUN apt-get update && \
	apt-get install --yes --no-install-recommends buildbot && \
	apt-get clean && \
	rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN mkdir /buildbot && \
	chown buildbot:buildbot /buildbot

USER buildbot
WORKDIR /buildbot

RUN buildbot create-master master && \
	mv master/master.cfg.sample master/master.cfg

EXPOSE 8010

ENTRYPOINT ["/usr/bin/buildbot"]
CMD ["start", "--nodaemon", "master"]
