# ICA 2 Bi623 #
I created a new git repository and cloned in the jupiter notebook 

Now I am going to create a new conda env : 

HINT: to use bash in jpnb add new code block and do 
```
! [code]
```

Talaps pathway: 
/projects/bgmp/calz/bioinfo/Bi623/ICA2

```
$ conda create -n bgmp_env

$ conda activate bgmp_env
```
## SRA ##
install SRA Tools: most recent vs  

```
conda install sra-tools 
```
check vs
```
$ fastq-dump --version

fastq-dump : 2.9.6
```

yikes ok updating 
```
$ conda update sra-tools 
```

ok didnt work I'm gunna remove and redownload w version specified 
```
$ conda remove sra-tools
$ conda install sra-tools=3.1.1
```
check vs
```
$ fastq-dump --version                                                                                                                               
                      
fastq-dump : 3.1.1
```


next use fastq-dump to download files
```
$ fastq-dump SRR849968                                                                                                                               
Read 57213 spots for SRR849968
Written 57213 spots for SRR849968  
```

```
$ fastq-dump SRR849828                                                                                                                               
Read 130034 spots for SRR849828 
Written 130034 spots for SRR849828    
```

add .gitignore file 

### Number of Seq per file ###
wrote a python code to count seq: 
```
Number of sequences in file ending in 828: 130034
Number of sequences in file ending in 968: 57213
```
### blast ###
modified above code to print out first 10 seq lines of each file and blasted them at online NCBI : 

https://blast.ncbi.nlm.nih.gov/Blast.cgi

**File 828 most likely match:**
PREDICTED: Syngnathus scovelli ribosomal protein S27a (rps27a), mRNA 

**File 968 most likely match:**
PREDICTED: Syngnathus typhle uncharacterized LOC133158031 (LOC133158031), transcript variant X3, mRNA

BUT: 
PREDICTED: Syngnathus scovelli uncharacterized LOC125978158 (LOC125978158), transcript variant X3, mRNA

is only .4% less likely and is the same species as file 828 so that is my best guess at the species in this fastq

## Ensemble 
 pull each file w wget: 
```
wget https://ftp.ensembl.org/pub/release-112/fasta/caenorhabditis_elegans/pep/Caenorhabditis_elegans.WBcel235.pep.all.fa.gz
wget https://ftp.ensembl.org/pub/release-112/fasta/homo_sapiens/pep/Homo_sapiens.GRCh38.pep.all.fa.gz
wget https://ftp.ensembl.org/pub/release-112/fasta/tetraodon_nigroviridis/pep/Tetraodon_nigroviridis.TETRAODON8.pep.all.fa.gz
wget https://ftp.ensembl.org/pub/release-112/fasta/saccharomyces_cerevisiae/pep/Saccharomyces_cerevisiae.R64-1-1.pep.all.fa.gz
```

to see if there are isoforms im comparing the total number of records with the number of unique gene ids -> if tehre are less unique genes than total unique proteins these are isoforms of the same gene 