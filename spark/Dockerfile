FROM centos:7

RUN rpm -i http://repos.mesosphere.io/el/7/noarch/RPMS/mesosphere-el-repo-7-1.noarch.rpm && \
yum -y install mesos-0.24.1 
RUN yum -y install java-1.7.0-openjdk
RUN curl http://d3kbcqa49mib13.cloudfront.net/spark-1.5.2-bin-hadoop2.6.tgz \
    | tar -xzC /opt && \
    mv /opt/spark* /opt/spark

COPY spark_conf/* /opt/spark/conf/
COPY scripts /scripts

ENV SPARK_HOME /opt/spark

ENTRYPOINT ["/scripts/run.sh"]
