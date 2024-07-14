FROM ubuntu:22.04

RUN apt-get update \
    && apt-get upgrade -y \
    && apt-get install -y software-properties-common \
    && apt-add-repository -y ppa:ansible/ansible \
    && apt-get update \
    && apt-get install -y ansible \
    && apt-get install -y python3 python3-argcomplete python3-pip python3-watchdog \
    && apt-get install -y git vim

RUN cd /tmp \
    && git clone https://github.com/zenoix/walnut-environment.git \
    && cd walnut-environment \
    && ansible-galaxy install -r requirements/common.yaml

ENTRYPOINT /bin/bash
