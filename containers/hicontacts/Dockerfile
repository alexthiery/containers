FROM  rocker/tidyverse:4.3.0

LABEL authors="eva.hamrud@crick.ac.uk" \
      description="Docker image containing R and R studio and HiContacts"

# Install apt packages
RUN apt-get update \
      && apt-get install -y --no-install-recommends \
      libxt-dev

# Install HiContacts
RUN   R -e "BiocManager::install('HiContacts', version = '3.12')"
