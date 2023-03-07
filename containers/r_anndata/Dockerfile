FROM  alexthiery/10x-npb-seurat:latest

LABEL authors="eva.hamrud@crick.ac.uk" \
      description="Docker image containing all requirements to run 10x downstream analysis in seurat + anndata for data conversion"

# Install anndata R library
RUN  R -e "install.packages('anndata')"

# Install anndata python module
RUN pip install anndata