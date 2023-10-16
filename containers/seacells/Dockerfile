FROM  nfcore/base:2.1

LABEL authors="eva.hamrud@crick.ac.uk" \
      description="Docker image containing requirements to run SEACELLS" 

RUN apt-get update
RUN apt-get install -y \
    libhdf5-dev \
    gcc

# Install the conda environment - removed SEACells + palantir commit tag as it wasnt working
COPY environment.yml /
RUN conda env create --quiet -f /environment.yml && conda clean -a

# Add conda installation dir to PATH (instead of doing 'conda activate')
ENV PATH /opt/conda/envs/seacells/bin:$PATH

# Dump the details of the installed packages to a file for posterity
RUN conda env export --name seacells > seacells.yml

# Add missing library
RUN pip install ipywidgets==8.0.6

# Install previous version of matplotlib due to clashes with scanpy
RUN pip install matplotlib==3.6.3

# Install older version of pandas which is compatible with scanpy 1.8.2
RUN pip install pandas==1.3.3


## From comparing seacells container v0.2 and v0.4:

# Install older version of importlib-metadata
RUN pip install importlib-metadata==6.5.0

# Install older version of notebook-shim
RUN pip install notebook-shim==0.2.2