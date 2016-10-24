FROM nvidia/cuda:8.0-cudnn5-devel-ubuntu16.04
MAINTAINER darrell-help@lists.eecs.berkeley.edu

RUN apt update && apt install -y --no-install-recommends \
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
        vim \
        emacs \
        nano \
        zsh \
        && \
    rm -rf /var/lib/apt/lists/*

ENV CAFFE_ROOT=/opt/caffe
WORKDIR $CAFFE_ROOT

RUN git clone --depth 1 https://github.com/cypof/caffe.git . && \
    git checkout 3c2c979e3864972ff6ae383467c913b659341050 && \
    for req in $(cat python/requirements.txt) pydot; do pip install $req; done && \
    mkdir build && cd build && \
    cmake -DUSE_CUDNN=1 .. && \
    make -j"$(nproc)"

ENV PYCAFFE_ROOT $CAFFE_ROOT/python
ENV PYTHONPATH $PYCAFFE_ROOT:$PYTHONPATH
ENV PATH $CAFFE_ROOT/build/tools:$PYCAFFE_ROOT:$PATH
RUN echo "$CAFFE_ROOT/build/lib" >> /etc/ld.so.conf.d/caffe.conf && ldconfig

