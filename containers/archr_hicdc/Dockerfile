FROM  alexthiery/archr:3.0

LABEL authors="eva.hamrud@crick.ac.uk" \
      description="Docker image with R4.1.2 and ArchR and HiC-DC+"

# Install HiCDCPlus
RUN   R -e "BiocManager::install('HiCDCPlus')"

# Install GenomicFeatures
RUN   R -e "BiocManager::install('GenomicFeatures')"

# Install Venn diagram plotter
RUN   R -e "install.packages('VennDiagram')"

# Install DESeq2
RUN   R -e "BiocManager::install('DESeq2')"