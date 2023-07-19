FROM  nfcore/base:2.1

LABEL authors="eva.hamrud@crick.ac.uk" \
      description="Docker image containing conda and HOMER"

RUN apt-get update
RUN apt-get install -y \
    libhdf5-dev \
    gcc

# # Create a conda environment
# RUN conda create --name homer python=3.5

# # Add conda installation dir to PATH (instead of doing 'conda activate')
# ENV PATH /opt/conda/envs/seacells/bin:$PATH

# Install homer
RUN conda install -c bioconda homer