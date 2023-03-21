FROM  nfcore/base:2.1

LABEL authors="alex.thiery@crick.ac.uk" \
      description="Docker image containing requirements to run SEACELLS"

RUN apt-get update
RUN apt-get install -y \
    libhdf5-dev \
    gcc

# Install the conda environment
COPY environment.yml /
RUN conda env create --quiet -f /environment.yml && conda clean -a

# Add conda installation dir to PATH (instead of doing 'conda activate')
ENV PATH /opt/conda/envs/seacells/bin:$PATH

# Dump the details of the installed packages to a file for posterity
RUN conda env export --name seacells > seacells.yml

# Add missing library
RUN pip install ipywidgets

# Install previous version of matplotlib due to clashes with scanpy
RUN pip install 'matplotlib<3.7'