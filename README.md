# StrainPhlan-COMP383
COMP 383 StrainPhlAn Project by Jay Pothuganti, Maryum Ahmad, Megan Martinez, Sneha Chowdhury

MetaPhlAn Github (https://github.com/biobakery/MetaPhlAn)


## Pivoting to StrainPhlAn
Due to usabiltiy issues with MAGinator and recurring errors, we've decided to try the computation tool StainPhlAn instead. 
Breifly, StrianPhlan works by reconstructing consensus sequence variants within species-specific marker genes and using them to estimate strain-level phylogenies. Although StrainPhlAn's functionality is a bit different from MAGinator's it will still be beneficial to get some output.

## Downloading MetaPhlAn (StrainPhlAn uses the output from MetaPhlAn)
          #Installing MetaPhlAn
          wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
          bash ~/Miniconda3-latest-Linux-x86_64.sh
          #after creating the conda environment the terminal needs to be reloaded
          conda install -c bioconda metaphlan
          conda create --name mpa -c bioconda python=3.7 metaphlan
          conda activate mpa
          pip install metaphlan
          #Downloading the library
          metaphlan --install --index mpa_vJan21_CHOCOPhlAnSGB_202103 --bowtie2db <database folder>

## StrainPhlAn Output
