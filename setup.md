---
title: Setup
---

## Downloading today's files

On the desktop, make a folder called `RNA-seq`.  Make another folder called `sleuth_files` inside `RNA-seq`.

```
cd ~/Desktop
mkdir RNA-seq
cd RNA-seq
mkdir sleuth_files
```

Download the zipped file in the kallisto dropbox link below.  From the sleuth dropbox link,
only download the `hi_seq.txt` file if you are not jumping straight into the sleuth part of the
tutorial.  Unzip the kallisto dropbox file into the `~/Desktop/RNA-seq` folder made earlier.  Move
the `hi_seq.txt` file into `~/Desktop/RNA-seq`.

For Kallisto files: https://www.dropbox.com/sh/n84n0n1i3sdi552/AAACLGmpM6cHiNF_MnXfwONDa?dl=0

For Sleuth files: https://www.dropbox.com/sh/diu7c7kmxec08bz/AAAZnRTjA2mlQwdnt060os5Ca?dl=0 



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

To make linux recognize the kallisto program and to make it executable from any folder, copy the
kallisto program into `/usr/local/bin/`.  The program will have to be made into an executable.

```
sudo cp kallisto /usr/local/bin/
cd /usr/local/bin/
sudo chmod +x kallisto
```




## To install Sleuth (Rstudio)

rhdf5 will be required from bioconductor to run sleuth.  Occasional first time installers may also
need fs.
```
BiocManager::install("rhdf5")
install.packages("fs")
```

Devtools should have been previously installed.  Install sleuth using:
```
devtools::install_github("pachterlab/sleuth")
library(sleuth)
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
