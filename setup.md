---
title: Setup
---

## To install Kallisto (bash)

Change directory to the Desktop.
```
cd ~/Desktop
```

Download kallisto by running the command below.  'linux' can be replaced with 'mac', or 'windows'
depending on the system.
```
wget https://github.com/pachterlab/kallisto/releases/download/v0.45.0/kallisto_linux-v0.45.0.tar.gz
```

Unpack the gzipped file using;
```
tar -zvxf kallisto_linux-v0.45.0.tar.gz 
```

By running 'ls', we a new folder in the Desktop.  This folder contains the Kallisto program.  Enter
this folder by typing;
```
cd kallisto_linux-v0.45.0
```

**NOTE**
If you are technically savy, and in your own time, you can try the method below under _OPTIONAL
APPROACH_ to make kallisto executable from anywhere.  For now, please follow the next step so that
everyone is on the same page.

One of the files in this folder is 'kallisto', and is what will enable the software programming we
will be completing. Make a folder for today's practical in the Home directory and copy kallisto into
it using the chained commands below.  Keep in mind that this particular command will only work if
you are in the same directory as kallisto.
```
mkdir ~/RNA-seq; cp ./kallisto ~/RNA-seq/
```

**OPTIONAL APPROACH**
For those who are technically savy, they can create alias in their .bashrc file.  You need to know
the path to the folder containing kallisto for this (type 'pwd' when in the right directory).  Go to
your home directory ('cd ~/'), and edit the .bashrc ('nano .bashrc').  Add this line somewhere:
```
alias kallisto='/path/to/folder/kallisto'
```

change /path/to/folder with the directory you found earlier using pwd.  Save the changes, close the
text editor, and type this:
```
source ~/.bashrc
```


## Downloading today's files

Today's files should be in the kallisto file you downloaded earlier.  Go to the kallisto file you
unpacked, and look for the folder 'Test'.

<!-- Once you have completed the above, download the files that will be used today  -->
<!-- ``` -->
<!-- wget ftp://ftp.ensembl.org/pub/current_fasta/homo_sapiens/cdna/Homo_sapiens.GRCh38.cdna.all.fa.gz -->
<!-- wget ftp://ftp.ensembl.org/pub/current_fasta/homo_sapiens/ncrna/Homo_sapiens.GRCh38.ncrna.fa.gz -->
<!-- cat Homo_sapiens.GRCh38.cdna.all.fa.gz Homo_sapiens.GRCh38.ncrna.fa.gz > Homo_sapiens.GRCh38.rna.fa.gz -->
<!-- ``` -->



## To install Sleuth (Rstudio)

rhdf5 will be required from bioconductor to run sleuth.
```
source("http://bioconductor.org/biocLite.R")
biocLite("rhdf5")
```

Devtools should have been previously installed.  Install sleuth using:
```
devtools::install_github("pachterlab/sleuth")
```

If devtools are missing, they can be installed by:
```
install.packages("devtools")
```



## To learn more
Kallisto has an offical page here: https://pachterlab.github.io/kallisto/

Sleuth has an official page here: https://pachterlab.github.io/sleuth/

(modified from https://pachterlab.github.io/kallisto/source, and https://scilifelab.github.io/courses/rnaseq/labs/kallisto)

{% include links.md %}
