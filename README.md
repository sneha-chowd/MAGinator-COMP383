# MAGinator-COMP383
COMP 383 MAGinator Project by Jay Pothuganti, Maryum Ahmad, Megan Martinez, Sneha Chowdhury

# Dependencies, Packages, and Programming Languages Used
Python

R

Mamba

Snakemake

MAGinator

GTDB-tk Database

-Genone Taxonomy Database

-Used by MAGinator to assign taxonomic classifications

# Preprocessing Before Running MAGinator
- Install Miniconda

          #in the terminal
          wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
          bash ~/Miniconda3-latest-Linux-x86_64.sh
          conda create -n maginator -c bioconda -c conda-forge snakemake mamba
          conda activate maginator
          pip install maginator
  
- Download and Unzip GTDB-tk Database Release 214 (MAGINATOR_database). This took about 72 hours.
  
          wget https://data.ace.uq.edu.au/public/gtdb/data/releases/release214/214.1/auxillary_files/gtdbtk_r214_data.tar.gz
          tar xvzf *.tar.gz
  
- Download data (will be amended later when we have our data from Dr. Putonti)

# Running the test data
1. Test data were retrieved from 3 samples at SRA: https://www.ncbi.nlm.nih.gov/sra?LinkName=bioproject_sra_all&from_uid=715601 with IDs dfc99c_A, f9d84e_A and 221641_A.
   This was done using wget, fasterq-dump
2. On the reads.csv file (required input for the tool, provided in the tool's test data) change the paths to the extracted fastq file
3. First Command Tried to Run Test Data: ```maginator --vamb_clusters clusters.tsv --reads reads.csv --contigs contigs.fasta --gtdb_db /home/project2/MAGINATOR_database/release214/ --output test_two```
