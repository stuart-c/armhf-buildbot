FROM armv7/armhf-ubuntu:latest

RUN apt-get update && \
	apt-get install -y buildbot-slave && \
	apt-get clean && \
	rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN mkdir /buildbot && \
	chown buildbot:buildbot /buildbot

USER buildbot
WORKDIR /buildbot

RUN buildslave create-slave slave buildmaster:9989 example-slave pass

ENTRYPOINT ["/usr/bin/buildslave"]
CMD ["start", "--nodaemon", "slave"]
