FROM  nfcore/base:1.12.1

LABEL authors="eva.hamrud@crick.ac.uk" \
      description="Docker image containing requirements to run SEACELLS"

# Install the conda environment
COPY environment.yml /
RUN conda env create --quiet -f /environment.yml && conda clean -a

# Add conda installation dir to PATH (instead of doing 'conda activate')
ENV PATH /opt/conda/envs/seacells_conda-1.0.0/bin:$PATH

# Dump the details of the installed packages to a file for posterity
RUN conda env export --name seacells_conda-1.0.0 > seacells_conda-1.0.0.yml
