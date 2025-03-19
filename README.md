# MAGinator-COMP383
COMP 383 MAGinator Project by Jay Pothuganti, Maryum Ahmad, Megan Martinez, Sneha Chowdhury

# Dependencies, Packages, Programming Languages Used
Python

R

Mamba

Snakemake

MAGinator

GTDB-tk Database

-Genone Taxonomy Database

-Used by MAGinator to assign taxonomic classifications

# Preprocessing Before MAGinator
- Install Conda
  
          #in the powershell
          wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
          bash ~/Miniconda3-latest-Linux-x86_64.sh
          conda create -n maginator -c bioconda -c conda-forge snakemake mamba
          conda activate maginator
          pip install maginator
  
- download and unzip GTDB-tk database release 214 (MAGINATOR_database) took about 72 hours
  
          wget https://data.ace.uq.edu.au/public/gtdb/data/releases/release214/214.1/auxillary_files/gtdbtk_r214_data.tar.gz tar xvzf *.tar.gz
  
- we downloaded test data, would want user to download test data as well (clarify later)
