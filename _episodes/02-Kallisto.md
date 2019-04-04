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

Build index

```
kallisto index -i transcripts.idx transcripts.fasta.gz
```


Quantification

```

```
