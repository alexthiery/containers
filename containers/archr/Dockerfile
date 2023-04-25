FROM  alexthiery/tidyverse_4.1.2:1.0.0

LABEL authors="eva.hamrud@crick.ac.uk" \
      description="Docker image with R4.1.2 and ArchR"


## Set up params for installation:
RUN   R -e "r <- getOption('repos')" && \
      R -e "r['CRAN'] <- 'http://cran.cnr.berkeley.edu/'" && \
      R -e "options(repos = r)" && \
      R -e "install.packages('BiocManager', repos = 'http://cran.us.r-project.org')" && \
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

## Other packages:
# Install other packages that are needed
RUN   R -e "require(devtools)" && \
      R -e "install_version('hexbin', version = '1.28.2')" && \
      R -e "install_version('gridExtra', version = '2.3')" && \
      R -e "install_version('getopt', version = '1.20.3')" && \
      R -e "install_version('optparse', version = '1.7.1')" && \
      R -e "install_version('pheatmap', version = '1.0.12')" && \
      R -e "install_version('patchwork', version = '1.1.1')" && \
      R -e "install_version('future', version = '1.24.0')" && \
      R -e "install_version('future.apply', version = '1.8.1')" && \
      R -e "install_version('clustree', version = '0.4.4')"