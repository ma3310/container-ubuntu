# Image: ma3310/ubuntu:22.04-devBox
# Build: docker buildx build -t ma3310/ubuntu:22.04-devBox .
FROM ubuntu:22.04

# Configure apt
ENV DEBIAN_FRONTEND=noninteractive
# Switch back to dialog for any ad-hoc use of apt-get
ENV DEBIAN_FRONTEND=dialog
ENV LANG=C.UTF-8
ENV LC_ALL=C.UTF-8

RUN ln -s /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
# ENV TZ=Asia/Shanghai  # Overwrite the timezone in the container

# net-tools: ifconfig
RUN apt-get update && apt-get upgrade -y && apt install -y \
    bash-completion \
    curl \
    dialog \
    iproute2 \
    iputils-ping \
    less \
    lynx \
    mariadb-client \
    mycli \
    net-tools \
    nmap \
    openssh-client \
    gpg \
    software-properties-common \
    vim \
    wget \
    zip \
    zsh 

# Add 3rd-part tools
RUN add-apt-repository -yn ppa:deadsnakes/ppa \
 && add-apt-repository -yn ppa:git-core/ppa \
 && add-apt-repository -yn ppa:ondrej/nginx \
 && add-apt-repository -yn ppa:ondrej/php \
 && add-apt-repository -y ppa:ondrej/apache2

RUN apt-get install -y git

# Zsh needs git, zip tools.
WORKDIR /root
RUN curl -sS https://cdn.jsdelivr.net/gh/ohmyzsh/ohmyzsh/tools/install.sh | bash
RUN sed 's/ZSH_THEME="robbyrussell"/#ZSH_THEME="robbyrussell"\nZSH_THEME="ys"/' .oh-my-zsh/templates/zshrc.zsh-template > .zshrc

RUN apt install -y \
    python3.9-full python3.10-full python3-pip python3.11-full python3.12-full python3.12-distutils

## Update pip
RUN python3.9 -m ensurepip \
 && python3.9 -m pip install --upgrade pip
RUN python3.11 -m ensurepip \
 && python3.11 -m pip install --upgrade pip
RUN python3.12 -m ensurepip \
 && python3.12 -m pip install --upgrade pip

RUN apt-get upgrade -y && apt-get clean && rm -rf /var/lib/apt/lists/*

