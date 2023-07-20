FROM  rocker/tidyverse:4.1.2

LABEL authors="eva.hamrud@crick.ac.uk" \
      description="Docker image containing R and R studio and extra apt and conda packages "

# Install apt packages
RUN apt-get update \
      && apt-get install -y --no-install-recommends \
      apt-utils \
      build-essential \
      libhdf5-dev \
      libboost-filesystem1.67-dev \
      libxtst6 \
      libxt-dev \
      libfontconfig1-dev \
      libfribidi-dev \
      libgsl0-dev \
      libbz2-dev \
      liblzma-dev

# Add conda to $PATH
ENV PATH /opt/conda/bin:$PATH

# Install miniconda
RUN wget --quiet https://repo.anaconda.com/miniconda/Miniconda3-py38_4.9.2-Linux-x86_64.sh -O ~/miniconda.sh && \
    /bin/bash ~/miniconda.sh -b -p /opt/conda && \
    rm ~/miniconda.sh && \
    /opt/conda/bin/conda clean -tipsy && \
    ln -s /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh && \
    echo ". /opt/conda/etc/profile.d/conda.sh" >> ~/.bashrc && \
    echo "conda activate base" >> ~/.bashrc

# Update conda and install phate
RUN   conda update -n base -c defaults conda

# Set default python for reticulate
RUN   echo 'RETICULATE_PYTHON = /opt/conda/bin/python' >> /usr/local/lib/R/etc/Renviron

# Set CRAN and BioC repositories for package installations
RUN   echo 'local({library(BiocManager); r <- repositories(); r["CRAN"] <- "https://cran.rstudio.com/"; options(repos = r)}); \
            options(HTTPUserAgent = sprintf("R/%s R (%s)", getRversion(), paste(getRversion(), R.version$platform, R.version$arch, R.version$os)))' >> /usr/local/lib/R/etc/Rprofile.site

## Set up BiocManager:
RUN   R -e "install.packages('BiocManager', repos = 'http://cran.us.r-project.org')" && \
      R -e "BiocManager::install(version = '3.14')" && \
      R -e "require(devtools)"

## Set up ArchR:
# Install ArchR
RUN   R -e "devtools::install_github('GreenleafLab/ArchR', ref='master', repos = BiocManager::repositories())"
# Install ArchR dependencies
RUN   R -e "ArchR::installExtraPackages()"

## Set up annotation packages: 
# Install GenomicFeatures
RUN   R -e "BiocManager::install('GenomicFeatures')"
# Install OrgDb 
RUN   R -e "if (!requireNamespace('org.Gg.eg.db', quietly = TRUE)){BiocManager::install('org.Gg.eg.db')}"
# Install UCSC genome (will have to change to ENSEMBL later)
RUN   R -e "if (!requireNamespace('BSgenome.Ggallus.UCSC.galGal6', quietly = TRUE)){BiocManager::install('BSgenome.Ggallus.UCSC.galGal6')}"
# Install JASPAR motif database
RUN   R -e "BiocManager::install('JASPAR2020')"

## Other packages:
# Install other packages that are needed
RUN   R -e "require(devtools)" && \
      R -e "devtools::install_version('hexbin', version = '1.28.2')" && \
      R -e "devtools::install_version('gridExtra', version = '2.3')" && \
      R -e "devtools::install_version('getopt', version = '1.20.3')" && \
      R -e "devtools::install_version('optparse', version = '1.7.1')" && \
      R -e "devtools::install_version('pheatmap', version = '1.0.12')" && \
      R -e "devtools::install_version('patchwork', version = '1.1.1')" && \
      R -e "devtools::install_version('future', version = '1.24.0')" && \
      R -e "devtools::install_version('future.apply', version = '1.8.1')" && \
      R -e "devtools::install_version('clustree', version = '0.4.4')"