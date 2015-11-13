From busybox:ubuntu-14.04
ADD https://releases.hashicorp.com/consul/0.5.2/consul_0.5.2_linux_amd64.zip /tmp/consul_0.5.2_linux_amd64.zip
RUN cd /bin && unzip /tmp/consul_0.5.2_linux_amd64.zip && chmod +x /bin/consul && rm /tmp/consul_0.5.2_linux_amd64.zip

ADD https://releases.hashicorp.com/consul/0.5.2/consul_0.5.2_web_ui.zip /tmp/consul_0.5.2_web_ui.zip
RUN mkdir /ui && cd /ui && unzip /tmp/consul_0.5.2_web_ui.zip && rm /tmp/consul_0.5.2_web_ui.zip && mv dist/* . && rm -rf dist

ADD ./config /consul_config/
ONBUILD ADD ./config /consul_config/

EXPOSE 8300 8301 8301/udp 8302 8302/udp 8400 8500 8600 8600/udp 53 53/udp
VOLUME ["/data"]

