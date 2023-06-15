FROM  rocker/tidyverse:4.3.0

LABEL authors="eva.hamrud@crick.ac.uk" \
      description="Docker image containing R and R studio and HiContacts"

# Install apt packages 
RUN apt-get update \
      && apt-get install -y --no-install-recommends \
      libxt-dev \
      libbz2-dev

# Install HiContacts
RUN   R -e "BiocManager::install('HiContacts', version = '3.17')"
RUN   R -e "BiocManager::install('HiContactsData', version = '3.17')"
RUN   R -e "BiocManager::install('rtracklayer', version = '3.17')"
