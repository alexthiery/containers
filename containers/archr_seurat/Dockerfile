FROM  alexthiery/archr:3.0

LABEL authors="eva.hamrud@crick.ac.uk" \
      description="Docker image with R4.1.2 and ArchR and Seurat5"

# Install curl
RUN apt-get update \
      && apt-get install -y --no-install-recommends \
      curl

# Install Seurat v5
RUN   R -e "remotes::install_github('satijalab/seurat', 'seurat5', quiet = TRUE, upgrade = 'always')"