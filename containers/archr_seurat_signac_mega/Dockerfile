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