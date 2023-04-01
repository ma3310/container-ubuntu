# Docker Hub: ma3310/ubuntu:22.04-tools
FROM ubuntu:22.04

ENV LANG=C.UTF-8
ENV LC_ALL=C.UTF-8
ENV TZ=Asia/Shanghai

# net-tools: ifconfig
RUN apt-get update && apt-get upgrade -y && apt install -y \
    curl \
    git \
    iproute2 \
    iputils-ping \
    less \
    lynx \
    mariadb-client \
    mycli \
    net-tools \
    nmap \
    openssh-client \
    software-properties-common \
    vim \
    wget \
    zsh \
 && apt-get clean && rm -rf /var/lib/apt/lists/*
