FROM  nfcore/base:2.1

LABEL authors="eva.hamrud@crick.ac.uk" \
      description="Docker image containing requirements for scenicplus"

# Install linux libraries
RUN apt-get update && apt-get install -y \
    libhdf5-dev \
    gcc \
    libbz2-dev \
    make \
    build-essential

# Set the working directory
WORKDIR /scenicplus

# Install scenicplus using conda
RUN git clone https://github.com/aertslab/scenicplus .
RUN pip install -e . --use-feature=2020-resolver

# Install jupyter notebook
RUN pip install jupyter