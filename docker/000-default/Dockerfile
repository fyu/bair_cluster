FROM nvidia/cuda:8.0-cudnn5-devel-ubuntu16.04
MAINTAINER darrell-help@lists.eecs.berkeley.edu

RUN apt-get update && apt-get install -y --no-install-recommends \
        build-essential \
        cmake \
        git \
        wget \
        libatlas-base-dev \
        libboost-all-dev \
        libgflags-dev \
        libgoogle-glog-dev \
        libhdf5-serial-dev \
        libleveldb-dev \
        liblmdb-dev \
        libopencv-dev \
        libprotobuf-dev \
        libsnappy-dev \
        protobuf-compiler \
        python-dev \
        python-numpy \
        python-pip \
        python-scipy \
        python-setuptools \
        vim \
        emacs \
        nano \
        zsh \
        sudo \
        openssh-server \
        && \
    pip install --upgrade pip && \
    rm -rf /var/lib/apt/lists/*
