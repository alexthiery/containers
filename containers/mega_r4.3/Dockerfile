FROM  rocker/tidyverse:4.3.0

LABEL authors="eva.hamrud@crick.ac.uk" \
      description="Docker image with R4.3.0 and scMEGA (+ seurat + ArchR)"

# Install apt packages
RUN apt-get update \
      && apt-get install -y --no-install-recommends \
      apt-utils \
      build-essential \
      libhdf5-dev \
      libxtst6 \
      libxt-dev \
      libfontconfig1-dev \
      libfribidi-dev \
      libgsl0-dev \
      libbz2-dev \
      liblzma-dev

# Set CRAN and BioC repositories for package installations
RUN   echo 'local({library(BiocManager); r <- repositories(); r["CRAN"] <- "https://cran.rstudio.com/"; options(repos = r)}); \
            options(HTTPUserAgent = sprintf("R/%s R (%s)", getRversion(), paste(getRversion(), R.version$platform, R.version$arch, R.version$os)))' >> /usr/local/lib/R/etc/Rprofile.site

## Set up BiocManager:
RUN   R -e "install.packages('BiocManager', repos = 'http://cran.us.r-project.org')" && \
      R -e "BiocManager::install(version = '3.14')" && \
      R -e "require(devtools)"

# Install R packages that are needed
RUN   R -e "require(devtools)" && \
      R -e "devtools::install_github('GreenleafLab/ArchR', ref='master', repos = BiocManager::repositories())" && \
      R -e "ArchR::installExtraPackages()" && \
      R -e "devtools::install_github('CostaLab/scMEGA')"  && \
      R -e "remotes::install_github('stuart-lab/signac', 'seurat5')" && \
      R -e "BiocManager::install('JASPAR2020')" && \
      R -e "devtools::install_version('hexbin', version = '1.28.2')" && \
      R -e "devtools::install_version('gridExtra', version = '2.3')" && \
      R -e "devtools::install_version('getopt', version = '1.20.3')" && \
      R -e "devtools::install_version('optparse', version = '1.7.1')" && \
      R -e "devtools::install_version('pheatmap', version = '1.0.12')" && \
      R -e "devtools::install_version('patchwork', version = '1.1.1')" && \
      R -e "devtools::install_version('future', version = '1.24.0')" && \
      R -e "devtools::install_version('future.apply', version = '1.8.1')" && \
      R -e "install.packages('VennDiagram')" && \
      R -e "BiocManager::install('ComplexHeatmap')" && \
      R -e "BiocManager::install('topGO')" && \
      R -e "BiocManager::install('clusterProfiler')"
