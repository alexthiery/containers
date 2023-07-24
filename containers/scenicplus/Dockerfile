FROM  nfcore/base:2.1

LABEL authors="eva.hamrud@crick.ac.uk" \
      description="Docker image containing requirements for scenicplus"

# Install linux libraries
RUN apt-get update
RUN apt-get install -y \
    libhdf5-dev \
    gcc \
    libbz2-dev \
    make \
    build-essential

# Install scenicplus using conda
RUN git clone https://github.com/aertslab/scenicplus
RUN cd scenicplus
RUN pwd -p
RUN ls -lah
RUN pip install -e . --use-feature=2020-resolver
