FROM  alexthiery/archr:2.0

LABEL authors="eva.hamrud@crick.ac.uk" \
      description="Docker image with R4.1.2 and ArchR and Macs2"

# Install MACS2 for peak calling: 
RUN   conda install -c anaconda pip && \
      pip install MACS2