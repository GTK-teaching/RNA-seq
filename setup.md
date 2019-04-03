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

Keep in mind that files generated using kallisto can be passed on to sleuth.  You can use the
command

```
wget DROPBOX-LINK
```

[For Kallisto files][https://www.dropbox.com/sh/n84n0n1i3sdi552/AAACLGmpM6cHiNF_MnXfwONDa?dl=0]

[For Sleuth files][https://www.dropbox.com/sh/diu7c7kmxec08bz/AAAZnRTjA2mlQwdnt060os5Ca?dl=0] 



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
