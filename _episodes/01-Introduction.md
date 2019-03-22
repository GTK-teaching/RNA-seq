---
title: "Introduction"
teaching: 15
exercises: 0
questions:
- "What is RNA-seq?"
- "What is alignment-free quantification?"
objectives:
- "Get acquinted with core concepts of RNA-seq"
keypoints:
- "RNA-seq is processed through tools such as Kallisto by alignment-free approaches.  This approach
has improved speeds over previous approaches requiring alignment"
---

# Introduction

## Kallisto

Kallisto is an "alignment free" RNA-seq quantification method.  Thanks to its approach using a
De Bruijn graph, it has noticeably smaller memory footprint.  It runs through the command-line.

Kallisto is geared towards quantification on the transcript (isoform) level, rather than the gene
level (although the latter can also be done by post-processing Kallisto output.) However, read
assignment to transcript isoforms cannot (in general) be done unambiguously, so there is an
intrinsic “quantification noise” or variability in this process. Kallisto can thus be run either in
a single step (which is very fast) or in “bootstrap” mode (which takes longer, but can be done on
several processors in parallel) in order to get uncertainty estimates for the expression levels - a
kind of error bars for the quantification process. Running with bootstraps is mandatory if you want
to perform differential expression analysis of isoforms with Sleuth (see below).

Kallisto is primarily meant for quantification of an existing set of FASTA sequences, that is, it
does not perform transcript assembly and it cannot quantify the expression of novel transcripts that
are not in the transcript index that you provide to it. With that said, you can of course use
contigs from an assembly that you have produced in some other program in your Kallisto index. It
would also be possible to use the software for e g metagenomics or metatranscriptomics
quantification.

## Sleuth

Sleuth is used for the differential expression analysis of transcript quantification.  It has been
developed to work best with Kallisto thanks to Kallisto's bootstraps, which can leverage technical
replicates to better determine differential expression.  Other tools also exist for differential
expression analysis, such as limma and DESeq2, to analyze the Kallisto ouput.  These tools may not
account for inherent variability as a result of Kallisto's transcript quantification.  Sleuth is
still in development.

As described above, Kallisto enables leveraging of technical replicates using bootstraps.

It is important to note that Sleuth is an R package, designed to make use of its graphical
capabilities.  At the end of this topic, we will introduce you to the graphical options available.


(This explanation was taken from
[https://scilifelab.github.io/courses/rnaseq/labs/kallisto][SciLifeLab github website] 
