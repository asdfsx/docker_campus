From asdfsx/mesos-base:0.26.0
MAINTAINER asdfsx <asdfsx@google.com>

RUN yum -y install marathon-0.13.0 && yum clean all 

CMD ["marathon", "--no-logger"]

COPY entrypoint.sh /

ENTRYPOINT ["/entrypoint.sh"]
