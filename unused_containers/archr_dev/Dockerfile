FROM  alexthiery/archr:3.0

LABEL authors="eva.hamrud@crick.ac.uk" \
      description="Docker image with R4.1.2 and ArchR dev version"

# Install curl
RUN apt-get update \
      && apt-get install -y --no-install-recommends \
      curl

# Install ArchR dev version
RUN   R -e "devtools::install_github('GreenleafLab/ArchR', ref='dev', repos = BiocManager::repositories())"
# Install ArchR dependencies
RUN   R -e "ArchR::installExtraPackages()"