FROM  nfcore/base:2.1

LABEL authors="alex.thiery@crick.ac.uk" \
      description="Docker image containing all requirements to run Seurat analysis - taken from seurat-docker on github"

RUN apt-get update
RUN apt-get install -y \
    libhdf5-dev \
    gcc

RUN pip3 install --upgrade pip
RUN pip3 install cmake
RUN pip3 install SEACells
RUN pip3 install notebook