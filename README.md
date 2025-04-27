# StrainPhlAn-COMP383
COMP 383 StrainPhlAn Project by Jay Pothuganti, Maryum Ahmad, Megan Martinez, Sneha Chowdhury

MetaPhlAn Github (https://github.com/biobakery/MetaPhlAn)

## Pivoting to StrainPhlAn
Due to usabiltiy issues with MAGinator and recurring errors, we've decided to try the computational tool StainPhlAn instead. 
Breifly, StrianPhlan works by reconstructing consensus sequence variants within species-specific marker genes and using them to estimate strain-level phylogenies. Although StrainPhlAn's functionality is a bit different from MAGinator's it will still be beneficial to get some output.

## Downloading MetaPhlAn
StrainPhlAn is a tool within the MetaPhlAn toolkit, requiring MetaPhlAn output. Therefore, MetaPhlAn installation is required before StrainPhlAn can be used. MetaPhlAn is installed using conda. To download conda:

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

MetaPhlAn uses a database that includes clade markers for its analysis. For ease of use, it is reccommended to deactivate the mpa environment when downloading the library. Additionally, we would further reccomend git cloning the MetaPhlAn repository and putting the database in their metaphlan_database folder, as doing so circumvents PATH issues with the database and errors of it unecessarily realoading. To download prior to running to the tool:
```
#Downloading the database
metaphlan --install --index mpa_vJan21_CHOCOPhlAnSGB_202103 --bowtie2db <database folder>
```


## Data
To test StrainPhlAn's strain-level identification, two urobiome metagenomic samples (8380 and 8330) each with 3 identified strains of _E. coli_ via Floria (https://github.com/bluenote-1577/floria) were used to determine StrainPhlAn's success. Due to StrainPhlAn's filtering requirements, at least 3 samples are required to successfully run and have identified strains. Therefore, two more samples were added, one identified with 1 strain of _E. coli_ (8517) and one with 3 strains (8525). These samples can be retrieved from the sample_data folder. 

## Running StrainPhlAn
Since multiple directories will be made an accessed in order to run StrainPhlAn, we reccomend to make a directory to house all the required files within the MetaPhlAn repository clone:
```
mkdir strainphlan_run
cd strainphlan_run
```

SAM files from MetaPhlAn are required input for StrainPhlAn. To create an individual SAM file: 
``` 
# replace <sample_number> with correct sample identifier, repeat the metaphlan command for each sample 
mkdir -p sams
metaphlan /path/to/forward/read.fastq,/path/to/reverse/read.fastq --bowtie2out <sample_number>.bowtie2.bz2 -s sams/<sample_number>.sam.bz2 --nproc 5 --input_type fastq -o <sample_number>_test_profiled.tsv
```

StrainPhlAn also requires consensus marker files as input, which is created from another function in the MetaPhlAn toolkit:
```
mkdir -p consensus_markers
sample2markers.py -i sams/*.sam.bz2 -o consensus_markers -n 8
```

For this analysis, we needed to extract markers of _E. coli_ from MetaPhlAn database. This will be used as input for StrainPhlAn:
```
mkdir -p db_markers
extract_markers.py -c t__SGB10068 -o db_markers/ #SGB10068 is the id for _E. coli_ in the MetaPhlAn database
```

Finally, a reference genome can optionally be included so that the StrainPhlAn run will filter the selected clade markers based on their presence in the reference-genome. For this analysis the _E.coli_ K-12 reference genome was used and can be downloaded via NCBI Datasets using the following command, but it is also included in the sample_data folder.
```
datasets download genome accession GCF_000005845.2
```
With all the required input created, to run StrainPhlAN:
```
strainphlan -s consensus_markers/*.json* -m db_markers/t__SGB10068.fna -r /path/to/reference/genome/GCF_000005845.2_ASM584v2_genomic.fna
-o strainphlan_output -n 8 -c t__SGB10068
```

## Output
For the purposes of our analysis, the most helpful output files are:
* RAxML_bestTree.t__SGB10068.StrainPhlAn4.tre - a Newick formatted Phylogenetic Tree of phylogenetic relationships between the dominant _E. coli_ strain identified in each sample
  * iTOL (https://itol.embl.de/) was used to visualize the Phylogenetic Tree 
* t__SGB10068.polymorphic - statistics on the polymorphic site

All expected output is included in the output folder. 
