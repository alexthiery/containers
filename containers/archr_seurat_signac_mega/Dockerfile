FROM  alexthiery/archr_macs2_seurat:3.0 

LABEL authors="eva.hamrud@crick.ac.uk" \
      description="Docker image with R4.1.2 and ArchR and Macs2 and seurat and signac and scMEGA v0.2.0"

# Install curl
RUN apt-get update \
      && apt-get install -y --no-install-recommends \
      cmake

# Install R packages
RUN   R -e "require(devtools)" && \
      R -e "remotes::install_github('stuart-lab/signac', 'seurat5')" && \
      R -e "devtools::install_github('CostaLab/scMEGA@fd1f9935108f7f3ebcc253403a6e0d4355887ae3')"  && \
      R -e "BiocManager::install('JASPAR2020')" && \
      R -e "devtools::install_version('pheatmap', version = '1.0.12')" && \
      R -e "install.packages('VennDiagram')" && \
      R -e "BiocManager::install('ComplexHeatmap')" && \
      R -e "BiocManager::install('topGO')" && \
      R -e "remotes::install_version('ggplot2', version='3.3.6')" && \
      R -e "BiocManager::install('clusterProfiler', ask = F, update = F)"