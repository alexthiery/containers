FROM  nfcore/base:2.1

LABEL authors="eva.hamrud@crick.ac.uk" \
      description="Docker image containing conda and HOMER"

RUN apt-get update
RUN apt-get install -y \
    libhdf5-dev \
    gcc

# Install the conda environment
COPY environment.yml /
RUN conda env create --quiet -f /environment.yml && conda clean -a

# Add conda installation dir to PATH (instead of doing 'conda activate')
ENV PATH /opt/conda/envs/seacells/bin:$PATH

# Install homer
RUN conda install -c bioconda homer