FROM registry:5000/default

ENV CAFFE_ROOT=/opt/caffe
WORKDIR $CAFFE_ROOT

RUN git clone --depth 1 --branch nccl --single-branch https://github.com/cypof/caffe.git . && \
    git checkout 35de71de18fbcd96f6555a2c55be0d108e9e986d && \
    cd python && for req in $(cat requirements.txt) pydot; do pip install $req; done && cd .. && \
    git clone https://github.com/NVIDIA/nccl.git && cd nccl && make -j install && cd .. && \
    mkdir build && cd build && \
    cmake -DUSE_CUDNN=1 -DUSE_NCCL=1 .. && \
    make -j"$(nproc)"

ENV PYCAFFE_ROOT $CAFFE_ROOT/python
ENV PYTHONPATH $PYCAFFE_ROOT:$PYTHONPATH
ENV PATH $CAFFE_ROOT/build/tools:$PYCAFFE_ROOT:$PATH
RUN echo "$CAFFE_ROOT/build/lib" >> /etc/ld.so.conf.d/caffe.conf && ldconfig

