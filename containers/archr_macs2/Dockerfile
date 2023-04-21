FROM  alexthiery/archr:2.0

LABEL authors="eva.hamrud@crick.ac.uk" \
      description="Docker image with R4.1.2 and ArchR and Macs2"

# Install MACS2 for peak calling: 
RUN   conda install -c anaconda pip && \
      wget https://github.com/macs3-project/MACS/archive/refs/tags/v2.2.7.1.tar.gz -O MACS.tar.gz && \
      tar -xvf MACS.tar.gz && \
      cd MACS-2.2.7.1 && \
      sed -i 's/install_requires = \[f"numpy>={numpy_requires}",\]/install_requires = \[f"numpy{numpy_requires}",\]/' setup.py && \
      pip install -e .