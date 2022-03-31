######################################
# Start of bitfusion
######################################

FROM nvcr.io/nvidia/tensorflow:19.03-py3

MAINTAINER James Brogan <someone@somewhere.com>
 
#  Set initial working directory
WORKDIR /home/bitfusion/downloads/


RUN apt-get install -y --no-install-recommends \
        wget uuid libjsoncpp1 librdmacm1 libssl-dev libibverbs1 libnuma1 libcapstone3 libnl-3-200 libnl-route-3-200 open-vm-tools && \
    rm -rf /var/lib/apt/lists/*

RUN cd /tmp && \
    curl -fSslL -O https://packages.vmware.com/bitfusion/ubuntu/20.04/bitfusion-client-ubuntu2004_4.5.1-9_amd64.deb && \
    apt-get install -y ./bitfusion-client-ubuntu2004_4.5.1-9_amd64.deb && \
    rm -rf /tmp/*
########################################