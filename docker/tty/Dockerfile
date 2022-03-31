#
# My TTY Example
#

FROM docker.io/library/ubuntu:20.04@sha256:bea6d19168bbfd6af8d77c2cc3c572114eb5d113e6f422573c93cb605a0e2ffb

ADD https://github.com/tsl0922/ttyd/releases/download/1.6.3/ttyd.x86_64 /usr/bin/ttyd
RUN chmod +x /usr/bin/ttyd

RUN apt-get update && apt-get install -y vim net-tools dnsutils curl wget apt-transport-https gnupg2 traceroute tcpdump jq iproute2 openssh-client bash-completion && apt-get -y upgrade && curl -s https://packages.cloud.google.com/apt/

ADD https://github.com/krallin/tini/releases/download/v0.19.0/tini /sbin/tini
RUN chmod +x /sbin/tini

RUN apt-get install -y --no-install-recommends uuid libjsoncpp1 librdmacm1 libssl-dev libibverbs1 libnuma1 libcapstone3 libnl-3-200 libnl-route-3-200 open-vm-tools && rm -rf /var/lib/apt/lists/*

RUN cd /tmp && curl -fSslL -O https://packages.vmware.com/bitfusion/ubuntu/20.04/bitfusion-client-ubuntu2004_4.5.1-9_amd64.deb && apt-get install -y ./bitfusion-client-ubuntu2004_4.5.1-9_amd64.deb && rm -rf /tmp/*

WORKDIR /root

RUN echo ". /usr/share/bash-completion/bash_completion" >> /etc/bash.bashrc
RUN echo "source <(kubectl completion bash)" >> /etc/bash.bashrc
RUN sed -i 's/#force_color_prompt=yes/force_color_prompt=yes/' /root/.bashrc

EXPOSE 7681
ENTRYPOINT ["/sbin/tini", "--"]
CMD ["ttyd", "bash"]

