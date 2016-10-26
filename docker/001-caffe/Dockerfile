FROM registry:5000/default

ENV CAFFE_ROOT=/opt/caffe
WORKDIR $CAFFE_ROOT

RUN git clone --depth 1 --branch master --single-branch https://github.com/BVLC/caffe.git . && \
    git checkout 4ba654f5c88c36ee8ba53964b7faf25c6d7010b4 && \
    cd python && for req in $(cat requirements.txt) pydot; do pip install $req; done && cd .. && \
    mkdir build && cd build && \
    cmake -DUSE_CUDNN=1 .. && \
    make -j"$(nproc)"

ENV PYCAFFE_ROOT $CAFFE_ROOT/python
ENV PYTHONPATH $PYCAFFE_ROOT:$PYTHONPATH
ENV PATH $CAFFE_ROOT/build/tools:$PYCAFFE_ROOT:$PATH
RUN echo "$CAFFE_ROOT/build/lib" >> /etc/ld.so.conf.d/caffe.conf && ldconfig

