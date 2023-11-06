FROM  nfcore/base:2.1

LABEL authors="eva.hamrud@crick.ac.uk" \
      description="Docker image containing requirements to run SEACELLS" 

RUN apt-get update
RUN apt-get install -y \
    libhdf5-dev \
    gcc

RUN pip install SEACells==0.3.3
RUN pip install palantir==1.3.1

# Add missing library
RUN pip install ipywidgets==8.0.6

# Install previous version of matplotlib due to clashes with scanpy
RUN pip install matplotlib==3.6.3

# Install older version of pandas which is compatible with scanpy 1.8.2
RUN pip install pandas==1.3.3

# Install jupyter notebook so can work interactively
RUN pip install notebook