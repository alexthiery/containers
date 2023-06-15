FROM  rocker/tidyverse:4.0.4

LABEL authors="eva.hamrud@crick.ac.uk" \
      description="Docker image with R4.0.4 and HiCBrick"

# Downgrade BiocManager to version 3.11
RUN   R -e "BiocManager::install(version = '3.11', ask=FALSE)"

# Install HiCBricks
RUN   R -e "BiocManager::install('HiCBricks', version = '3.11')"