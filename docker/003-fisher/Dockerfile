FROM nvidia/cuda:8.0-cudnn5-devel-ubuntu16.04
MAINTAINER i@yf.io

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
        tmux \
        python3-dev \
        python3-numpy \
        python3-pip \
        python3-scipy \
        python3-setuptools \
        python3-tk \
        htop \
        rsync \
        curl \
        && \
    pip install --upgrade pip && \
    pip3 install --upgrade pip && \
    pip3 install matplotlib h5py lmdb Cython scikit-image ipython \
        networkx nose pandas python-dateutil protobuf Pillow six python-gflags

RUN pip3 install https://s3.amazonaws.com/pytorch/whl/cu80/torch-0.1.8.post1-cp35-cp35m-linux_x86_64.whl && \
    pip3 install torchvision

RUN apt-get install -y llvm-3.8 libedit-dev
ENV LLVM_CONFIG /usr/bin/llvm-config-3.8
RUN pip3 install llvmlite numba
