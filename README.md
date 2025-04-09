# MAGinator-COMP383
COMP 383 MAGinator Project by Jay Pothuganti, Maryum Ahmad, Megan Martinez, Sneha Chowdhury

MAGinator Github (https://github.com/Russel88/MAGinator?tab=readme-ov-file)

## Dependencies, Packages, and Programming Languages Used
Python

R

Mamba

Snakemake

MAGinator

GTDB-tk Database (found on the MAGinator github)
- Genome Taxonomy Database
- Used by MAGinator to assign taxonomic classifications

## Before Running MAGinator
- Install Miniconda (snakemake and mamba are included with this) 

          #in the terminal
          wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
          bash ~/Miniconda3-latest-Linux-x86_64.sh
          conda create -n maginator -c bioconda -c conda-forge snakemake mamba
          conda activate maginator
          pip install maginator
  
- Download and Unzip GTDB-tk Database Release 214 (MAGINATOR_database). This took about 72 hours.
  
          wget https://data.ace.uq.edu.au/public/gtdb/data/releases/release214/214.1/auxillary_files/gtdbtk_r214_data.tar.gz
          tar xvzf *.tar.gz
  
- git clone the MAGinator GitHub repo
  
          git clone https://github.com/Russel88/MAGinator.git
  - Activate MAGinator

          conda activate maginator

- Check if MAGinator and conda were properly installed

          maginator -h

- Your command line should look like this, waiting for your next command:

          (maginator) YourUsername@newton:~$

## Running the test data
1. Test data were retrieved from 3 samples at SRA: https://www.ncbi.nlm.nih.gov/sra?LinkName=bioproject_sra_all&from_uid=715601 with IDs dfc99c_A, f9d84e_A and 221641_A.
   This was done using wget, fasterq-dump
2. On the reads.csv file (required input for the tool, provided in the tool's test data) change the paths to the extracted fastq files forward and reverse reads
3. Unzip the contigs.fasta.gz file in the test_data directory
4. First Command Tried to Run Test Data: ```maginator --vamb_clusters clusters.tsv --reads reads.csv --contigs contigs.fasta --gtdb_db /home/project2/MAGINATOR_database/release214/ --output test_two```
   * Issue: Ran for 5 days and appeared to have been caught up, job terminated
5. Second Command Tried to Run Test Dta: ```maginator --vamb_clusters clusters.tsv --reads reads.csv --contigs contigs.fasta --gtdb_db /home/project2/MAGINATOR_database/release214/ --output test_out3 --max_cores 5 --max_mem 50 ```
   * Specified the number of cores and amount of memory allocated to the job to see if that would progress the job further

## Test Run Failure & Incompatible Server Type
The MAGinator github (https://github.com/Russel88/MAGinator?tab=readme-ov-file) states that "MAGinator can run on compute clusters using qsub (torque), sbatch (slurm), or drmaa structures." After letting the test data run for over two weeks with no success, we've come to the conclusion that "can run" actually means "must run" and that this tool is uncompatible with non-cluster servers. 
