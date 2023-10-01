FROM  alexthiery/archr_macs2_seurat:3.0 

LABEL authors="eva.hamrud@crick.ac.uk" \
      description="Docker image with R4.1.2 and ArchR and Macs2 and seurat and signac and scMEGA"

# Install curl
RUN apt-get update \
      && apt-get install -y --no-install-recommends \
      cmake

# Install R packages
RUN   R -e "require(devtools)" && \
      R -e "devtools::install_github('CostaLab/scMEGA')" && \
      R -e "remotes::install_github('stuart-lab/signac', 'seurat5')" && \
      R -e "BiocManager::install('JASPAR2020')" && \
      R -e "devtools::install_version('pheatmap', version = '1.0.12')" && \
      R -e "install.packages('VennDiagram')" && \
      R -e "BiocManager::install('ComplexHeatmap')" && \
      R -e "BiocManager::install('topGO')" && \
      R -e "BiocManager::install('clusterProfiler')"