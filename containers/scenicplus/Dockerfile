FROM  nfcore/base:2.1

LABEL authors="eva.hamrud@crick.ac.uk" \
      description="Docker image containing requirements for scenicplus"

# Install scenicplus using conda
RUN git clone https://github.com/aertslab/scenicplus
RUN cd scenicplus
RUN pip install -e .