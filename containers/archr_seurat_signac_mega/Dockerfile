FROM  alexthiery/archr_macs2_seurat:3.0 

LABEL authors="eva.hamrud@crick.ac.uk" \
      description="Docker image with R4.1.2 and ArchR and Macs2 and seurat and signac and scMEGA"

# Install curl
RUN apt-get update \
      && apt-get install -y --no-install-recommends \
      cmake

# Install signac
RUN   R -e "install.packages('Signac')"

# Install scMEGA
RUN R -e "library(devtools)"
RUN R -e "devtools::install_github('CostaLab/scMEGA')"

# Install slightly older Signac
RUN R -e "devtools::install_version(package = 'Signac', version = package_version('1.9.0'))"