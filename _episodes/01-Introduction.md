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

Kallisto uses pseudo-alignment for RNA-seq quantification.  Previous quantifiers attempted to align
reads to the genome to measure transcript expression.  The position of each read would have to be
checked against each part of the reference before quantification.  Tools such as Kallisto, Salmon,
and sailfish are part of a new generation using pseudo alignments for greatly improved speeds and
accurate results.

Pseudo-alignment is not reference-free.  Pseudo-alignments do not depend on aligning reads to each
position, but do require a reference to quantify expression levels.  Kallisto quantifies reads through a
de Bruijn graph.  Each read is broken into k-mers, and mapped by points of greatest overlap, or
k-mer k-compatibility class, as seen in Fig.1 below.  This approach means that quantifications is
done at the transcript level instead of gene level as with previous aligners.

![**Fig.1** Alt TextOverview of kallisto. The input consists of a reference transcriptome and reads from an RNA-seq experiment. (a) An example of a read (in black) and three overlapping transcripts with exonic regions as shown. (b) An index is constructed by creating the transcriptome de Bruijn Graph (T-DBG) where nodes (v1, v2, v3, … ) are k-mers, each transcript corresponds to a colored path as shown and the path cover of the transcriptome induces a k-compatibility class for each k-mer. (c) Conceptually, the k-mers of a read are hashed (black nodes) to find the k-compatibility class of a read. (d) Skipping (black dashed lines) uses the information stored in the T-DBG to skip k-mers that are redundant because they have the same k-compatibility class. (e) The k-compatibility class of the read is determined by taking the intersection of the k-compatibility classes of its constituent k-mers.  [From Bray et al. Near-optimal probabilistic RNA-seq quantification, Nature Biotechnology, 2016.]](../fig/deBruijn.png) 

An advantage of using kallisto is bootstrapping.  Bootstrapping can be used to improve statistical
deductions.  This is used during differential expression analysis in sleuth.  A disadvantage is that
as kallisto uses pseudo-alignment, it is not as capable in quantifying unknown or novel transcripts.

## Sleuth

Sleuth is used for the differential expression analaysis of transcript quantification.  While it can
work with the output of other quantifiers, Kallisto and sleuth have been designed to work
efficiently together.  For example, Sleuth makes use of Kallisto's bootstraps to leverage technical
replicate data in determining differentially expressing genes.  

It is important to note that Sleuth is an R package, designed to make use of its graphical
capabilities.  At the end of this topic, we will introduce you to the graphical options available.
