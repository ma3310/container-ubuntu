# Ubuntu Images

Normally when people start ubuntu container, they want to check system stutus or network environment, but original offical Ubuntu images are lack of necessary tools by default. This repository integrates essential diagnostic tools from official and most famous 3rd part repositories, and is connected to Docker Hub to provide handy images.

Access related Docker images at https://hub.docker.com/r/ma3310/ubuntu.

## ma3310/ubuntu:20.04-tools

Image ma3310/ubuntu:20.04-tools integrates below tools are from official repository:

| Package       | Command  | Function                  |
|---------------|----------|---------------------------|
| curl          | curl     |                           |
| iputils-ping  | ping     |                           |
| mycli         | mycli    | MySQL/MariaDB client tool |
| net-tools     | ifconfig |                           |
|               | netstat  |                           |
|               | route    |                           |

### Usage

#### Docker

``` bash
# Container will be automatically removed after issue exit command.
docker run --rm -it ma3310/ubuntu:20.04-tools

# Use own zsh environment to initilize console settings.
docker run --rm -it -v ~/:/root ma3310/ubuntu:20.04-tools /bin/zsh

# Diagnose localhost envrionment.
docker run --rm -it --network=host -v ~/:/root ma3310/ubuntu:20.04-tools /bin/zsh

# Diagnose docker/compose network envrionment.
docker run --rm -it --network=csk_default -v ~/:/root ma3310/ubuntu:20.04-tools /bin/zsh
```

#### Kubernets
```bash
# Pod will be automatically removed after issue exit command
kubectl run -i --tty --image=ma3310/ubuntu:20.04-tools --restart=Never --rm=true ubuntu-20.04-tools
```

## Official 20.04
``` bash
# 根据官方镜像 ubuntu:20.04 启动容器
docker run --rm -it ubuntu:20.04
```


## Build your own images

Users could also use Dockerfiles in this repository to build and release own images through docker commands.

``` bash
# Login Docker Hub.
docker login

# Build / Publish / Deploy images.
docker build . -t ma3310/ubuntu:20.04-tools
docker push ma3310/ubuntu:20.04-tools
docker pull ma3310/ubuntu:20.04-tools
```