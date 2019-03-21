---
title: Setup
---

## To install Kallisto (bash)

Install the following pre-requisites (the following commands have been written so as to be chained together):

```
sudo apt-get install cmake -y;
sudo apt-get install zlib1g-dev -y;
sudo apt-get install autoconf -y;
sudo apt-get install libhdf5-dev -y
```

Kallisto will be installed from the source files, which can be found on github or IVLE.  If you have
github set up, go to your Desktop and download files using:
```
git clone https://github.com/pachterlab/kallisto.git
```
Otherwise, they are in IVLE, under Practical materials, RNA-seq.  Unpack them into a folder called
kallisto on the Desktop

Moving to the source directory:
```
cd kallisto
Make htslib
```

Run autoconf on ext/htslib: (note, this only needs to be done once, not when you recompile):
```
cd ext/htslib
autoheader
autoconf
cd ../..
```

For old Linux systems, if you get an error reporting thread_pool.c:658:38: error: ‘PTHREAD_MUTEX_RECURSIVE’ undeclared (first use in this function).

you might need to make htslib using this command in the htslib folder.
```
make -j CFLAGS=-D_GNU_SOURCE lib-static
Build kallisto
```

Make a build directory and move there:
```
mkdir build
cd build
```

Run cmake:
```
cmake ..
```

Build the code:
```
make
```

The kallisto executable is now located in build/src. To install kallisto into the cmake install prefix path type:
```
make install
```

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

Install devtools by:
```
install.packages("devtools")
```



## To learn more
Kallisto has an offical page here: https://pachterlab.github.io/kallisto/
Sleuth has an official page here: https://pachterlab.github.io/sleuth/

(modified from https://pachterlab.github.io/kallisto/source)
{% include links.md %}
