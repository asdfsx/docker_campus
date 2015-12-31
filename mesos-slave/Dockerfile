From asdfsx/mesos-base:0.24.1
MAINTAINER asdfsx <asdfsx@google.com>

RUN curl -fLsS https://get.docker.com/ | sh

CMD ["/usr/sbin/mesos-slave"]

COPY entrypoint.sh /

ENTRYPOINT ["/entrypoint.sh"]
