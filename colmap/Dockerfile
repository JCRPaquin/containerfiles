FROM nvcr.io/nvidia/cuda:12.0.0-cudnn8-devel-ubuntu22.04

RUN apt-get update && apt-get install -y \
    git \
    cmake \
    ninja-build \
    build-essential \
    libopenblas-dev \
    libboost-program-options-dev \
    libboost-filesystem-dev \
    libboost-graph-dev \
    libboost-system-dev \
    libboost-test-dev \
    libgoogle-glog-dev \
    libeigen3-dev \
    libflann-dev \
    libfreeimage-dev \
    libmetis-dev \
    libgoogle-glog-dev \
    libgflags-dev \
    libsqlite3-dev \
    libglew-dev \
    qtbase5-dev \
    libqt5opengl5-dev \
    libcgal-dev \
    libtbb-dev \
    gcc-10 \
    g++-10 \
    python3-pip

ENV CC=/usr/bin/gcc-10
ENV CXX=/usr/bin/g++-10
ENV CUDAHOSTCXX=/usr/bin/g++-10

RUN git clone --recursive https://github.com/DrTimothyAldenDavis/SuiteSparse
RUN cd SuiteSparse && \
    git checkout "tags/v7.0.0" && \
    make && \
    make install && \
    cd .. && \
    rm -rf SuiteSparse

RUN git clone https://github.com/ceres-solver/ceres-solver
RUN cd ceres-solver && \
    mkdir build && \
    cd build && \
    cmake .. && \
    make -j10 && \
    make install && \
    cd .. && \
    rm -rf ceres-solver

RUN git clone https://github.com/colmap/colmap.git
RUN cd colmap && \
    mkdir build && \
    cd build && \
    cmake .. -GNinja -DCMAKE_CUDA_ARCHITECTURES=86 && \
    ninja && \
    ninja install && \
    cd .. && rm -rf colmap

RUN git clone --recursive https://github.com/jcrpaquin/pycolmap.git
RUN cd pycolmap && \
    pip install . && \
    cd .. && rm -rf pycolmap

RUN pip install numpy
