FROM  alexthiery/archr_macs2_seurat:3.0 

LABEL authors="eva.hamrud@crick.ac.uk" \
      description="Docker image with R4.1.2 and ArchR and Macs2 and seurat and signac and scMEGA"

# Install curl
RUN apt-get update \
      && apt-get install -y --no-install-recommends \
      cmake

# Install scMEGA
RUN R -e "library(devtools)"
RUN R -e "devtools::install_github('CostaLab/scMEGA')"

# Install Seurat v5 and latest Signac
RUN   R -e "remotes::install_github('stuart-lab/signac', 'seurat5')"

# Install JASPAR motif database (it should already be installed in the base image 'archr' but cant load it from this image)
RUN   R -e "BiocManager::install('JASPAR2020')"

# Install Venn diagram plotter
RUN   R -e "install.packages('VennDiagram')"

# Install pheatmap
RUN   R -e "devtools::install_version('pheatmap', version = '1.0.12')"

# Install complex heatmap
RUN   R -e "BiocManager::install('ComplexHeatmap')"

# Install packages to GO analysis
RUN R -e "BiocManager::install('topGO')"
RUN R -e "BiocManager::install('clusterProfiler')"