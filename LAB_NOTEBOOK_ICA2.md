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