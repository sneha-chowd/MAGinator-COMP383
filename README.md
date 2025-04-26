# StrainPhlan-COMP383
COMP 383 StrainPhlAn Project by Jay Pothuganti, Maryum Ahmad, Megan Martinez, Sneha Chowdhury

MetaPhlAn Github (https://github.com/biobakery/MetaPhlAn)


## Pivoting to StrainPhlAn
Due to usabiltiy issues with MAGinator and recurring errors, we've decided to try the computational tool StainPhlAn instead. 
Breifly, StrianPhlan works by reconstructing consensus sequence variants within species-specific marker genes and using them to estimate strain-level phylogenies. Although StrainPhlAn's functionality is a bit different from MAGinator's it will still be beneficial to get some output.

## Downloading MetaPhlAn
StrainPhlAn is a tool within the MetaPhlAn tool, requiring MetaPhlAn output. Therefore, MetaPhlAn installation is required before StrainPhlAn can be used. MetaPhlAn is installed using conda. To download conda:

```
#Installing Miniconda
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash ~/Miniconda3-latest-Linux-x86_64.sh
#after creating the conda environment the terminal needs to be reloaded
```

To install MetaPhlan via conda:
```
conda install -c bioconda metaphlan
conda create --name mpa -c bioconda python=3.7 metaphlan
conda activate mpa
```

MetaPhlAn uses a database that includes clade markers for its analysis. To download prior to running to the tool:
```
#Downloading the library
metaphlan --install --index mpa_vJan21_CHOCOPhlAnSGB_202103 --bowtie2db <database folder>
```

## Data
To test StrainPhlAn's strain-level identification, two urobiome metagenomic samples (8380 and 8330) each with 3 identified strains of _E. coli_ via Floria (https://github.com/bluenote-1577/floria) were used to determine StrainPhlAn's success. Due to StrainPhlAn's filtering requirements, at least 3 samples are required to successfully run and have identified strains. Therefore, two more samples were added, one identified with 1 strain of _E. coli_ (8517) and one with 3 strains (8525). These samples can be retrieved from the sample_data folder. 

## Running StrainPhlAn
SAM files from MetaPhlAn are required input for StrainPhlAn. To create SAM files: 
``` 
# replace <sample_number> with correct sample identifier
mkdir sams
metaphlan /path/to/forward/read.fastq,/path/to/reverse/read.fastq --bowtie2out <sample_number>.bowtie2.bz2 -s sams/<sample_number>.sam.bz2 --nproc 5 --input_type fastq -o <sample_number>_test_profiled.tsv
```



