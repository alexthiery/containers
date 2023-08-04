FROM  alexthiery/archr:3.0

LABEL authors="eva.hamrud@crick.ac.uk" \
      description="Docker image with R4.1.2 and ArchR and Macs2"

# Install MACS2 for peak calling: 
RUN   conda install -c anaconda pip && \
      wget https://github.com/macs3-project/MACS/archive/refs/tags/v2.2.7.1.tar.gz -O MACS.tar.gz && \
      tar -xvf MACS.tar.gz && \
      cd MACS-2.2.7.1 && \
      sed -i 's/install_requires = \[f"numpy>={numpy_requires}",\]/install_requires = \[f"numpy{numpy_requires}",\]/' setup.py && \
      pip install -e .

# Install curl
RUN apt-get update \
      && apt-get install -y --no-install-recommends \
      curl

# Install Seurat v5 and latest Signac
RUN   R -e "remotes::install_github('stuart-lab/signac', 'seurat5')"