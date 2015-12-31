From asdfsx/mesos-base:0.26.0
MAINTAINER asdfsx <asdfsx@google.com>

RUN curl -fLsS https://get.docker.com/ | sh

CMD ["/usr/sbin/mesos-slave"]

COPY entrypoint.sh /

ENTRYPOINT ["/entrypoint.sh"]
