FROM jcrpaquin/hloc

RUN apt-get update && apt install -y wget

RUN git clone --recursive https://github.com/cvg/pixel-perfect-sfm
RUN cd pixel-perfect-sfm && \
    pip install -r requirements.txt && \
    pip install . && \
    cd .. && \
    rm -rf pixel-perfect-sfm
