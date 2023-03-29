FROM jcrpaquin/colmap

RUN apt-get update && apt-get install -y \
    libhdf5-dev

RUN git clone --recursive https://github.com/cvg/Hierarchical-Localization/
RUN cd Hierarchical-Localization && \
    pip install -e .

