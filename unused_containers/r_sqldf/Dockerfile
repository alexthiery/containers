FROM  alexthiery/10x-npb-seurat:latest

LABEL authors="eva.hamrud@crick.ac.uk" \
      description="Docker image containing all requirements to run 10x downstream analysis in seurat + sqldf"

RUN apt-get update
RUN apt-get install -y \
    tcl tk

# Install sqldf R library
RUN  R -e "install.packages('sqldf')"