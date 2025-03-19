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
- install conda
  
          #in the powershell
          wget "https://repo.anaconda.com/archive/Anaconda3-2024.10-1-Windows-x86_64.exe" -outfile "./Downloads/Anaconda3-2024.10-1-Windows-x86_64.exe"
          pip install maginator
  
- download and unzip GTDB-tk database release 214 (MAGINATOR_database) took about 72 hours
  
          wget https://data.ace.uq.edu.au/public/gtdb/data/releases/release214/214.1/auxillary_files/gtdbtk_r214_data.tar.gz tar xvzf *.tar.gz
  
- we downloaded test data, would want user to download test data as well (clarify later)
