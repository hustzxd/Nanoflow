FROM nvcr.io/nvidia/cuda:12.8.1-cudnn-devel-ubuntu22.04

RUN sed -i 's|http://archive.ubuntu.com/ubuntu/|http://mirrors.aliyun.com/ubuntu/|g' /etc/apt/sources.list \
    && sed -i 's|http://security.ubuntu.com/ubuntu/|http://mirrors.aliyun.com/ubuntu/|g' /etc/apt/sources.list \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

ARG USERNAME=zxd
ARG UID=2011
ARG GID=2011

RUN groupadd -g ${GID} ${USERNAME} \
    && useradd -m -u ${UID} -g ${GID} -s /bin/bash ${USERNAME}

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
    vim \
    screen \
    htop \
    zsh \
    openssh-server \
    curl \
    git \
    pybind11-dev \
    liburing-dev \
    libopenmpi-dev \
    && rm -rf /var/lib/apt/lists/*

USER ${USERNAME}
WORKDIR /home/${USERNAME}
