---
title: "Using Kallisto"
teaching: 15
exercises: 0
questions:
objectives:
- "Introduction to Kallisto"
keypoints:
---

# What is Kallisto

Kallisto is a program for the quantification of RNA-seq using pseudo-alignment.  The program makes
use of an index to generate the pseudo-alignments, enabling quantification of transcript
abundances.  Indexing, pseudo-alignments, and quantification are not impacted by
bootstrapping.  Gains from bootstrapping are seen during differential gene analysis.  Quantification
is measured in Transcripts per Million (TPM).

# Getting started with Kallisto

Files used here are downloaded as described in Setup, as well as how kallisto was set up Kallisto.

The first step will be to generate an index.  This will generate de bruijn graphs for k-mers.

```
kallisto index -i saccer3.idx Saccharomyces_cerevisiae.R64-1-1.cdna.all.fa.gz
```

Quantification is a long process for the files we have.  We will generate a bash file as below to
enable kallisto quantification in the background.

```
kallisto quant -t 4 -i saccer3.idx -o wildtype.1 -b 30 SRR4018567_1.fastq SRR4018567_2.fastq
kallisto quant -t 4 -i saccer3.idx -o wildtype.2 -b 30 SRR4018568_1.fastq SRR4018568_2.fastq
kallisto quant -t 4 -i saccer3.idx -o wildtype.3 -b 30 SRR4018569_1.fastq SRR4018569_2.fastq

kallisto quant -t 4 -i saccer3.idx -o snf2.mutant.1 -b 30 SRR4018573_1.fastq SRR4018573_2.fastq
kallisto quant -t 4 -i saccer3.idx -o snf2.mutant.2 -b 30 SRR4018574_1.fastq SRR4018574_2.fastq
kallisto quant -t 4 -i saccer3.idx -o snf2.mutant.3 -b 30 SRR4018575_1.fastq SRR4018575_2.fastq
```

# Understanding Kallisto output

## Output files

In the new output file, you should have an HDF5 and json file.  The json file will contain a summary
of how kallisto was run.  The HDF5 file contains information used in differential gene analysis.
This file contains the bootstrap information.



<!-- ## Three parts -->

<!-- Kallisto can be divided into three parts: -->

<!-- 1. Indexing -->
<!-- 2. Pseudo-alignment -->
<!-- 3. Quantification -->



## TPMS

Results of Kallisto readings are in TPM.  TPM normalizes the data.

18:03.09
13:39.74
