
## Goals ##

- Quantification of transposable elements expression
- Bring attention to the fact that people are missing part of the transcriptome (!)

## Desirable characteristics and Considerations ##

- Must be easy to perform the analysis (anyone can use it)
  - Portability
- Can be installed with [Bioconda](https://bioconda.github.io/user/install.html)
- It's command line in the surface but [snakemake](https://snakemake.readthedocs.io/en/stable/) underneath.
  - [Improved workflows-as-applications](http://ivory.idyll.org/blog/2020-improved-workflows-as-applications.html): tips and tricks for building applications on top of snakemake

- We should aim to use scTELESCOPE on any data (from any pipeline). Consider that the single-cell world is changing fast.
  - 10x
  - smart-seq

- What is the next tool downstream of scTELESCOPE? (which should be the output format?)
  - [Seurat](https://satijalab.org/seurat/articles/get_started.html) (i.e. how do we tell Seurat about our HERVs?)

- Should we aim to have the option of running scTELESCOPE starting at different points? i.e.
  - sequencing reads
  - BAM with multi-mapping reads

- Can we use ATAC-seq or CITE-seq single-cell data?
- Explore aligning to a reference transcriptome.
  - [Azimuth](https://satijalab.org/azimuth/) ("App for reference-based single-cell analysis"). The [references](https://azimuth.hubmapconsortium.org/) are (Human) PBMC, Motor Cortex, Pancreas, Fetal Development, Lung, Kidney.
  - Importance of annotation. In the [Wang paper](https://genome.cshlp.org/content/early/2020/12/21/gr.265173.120.abstract) they use de novo assembly; is this data correct? how is the annotation affecting quantification?

- The dropout problem in scRNA-seq data
  - How is it a factor for TEs?
  - Do we see nothing because a TE or rare transcript is really absent or because it's so uncommon?

- How is the level of TEs compared to protein coding genes in scRNA-seq?



## Design ##

- scTELESCOPE has TELESCOPE at its heart
  - Get BAMs from single-cell data
  - Parallel run of TELESCOPE on each
- Is it posisble to run TELESCOPE on a multi-cell BAM?
- Are single cell RNA-seq reads always in **one** side of the PE sequencing (i.e. in one single read)?
    - "reads are paired because they reference the same "lecture" of the transcript but each file contains different info. R1 files contain both cell and UMI barcodes, and R2 contains the cDNA read of the transcript (And index files the sample barcode, although in most cases when analysing data from repositories it tends to come demultiplexed already so it's not needed). In the Human cell atlas we've considered it single-end because of this, but there is no consensus amongst the different archives/single cell services." From Enrique Sapena Ventura (a Data wrangler from HCA).
    - "there are so many techniques that stating that it will always be the case is probably lying. I can say that, for what I've seen, that the vast majority of data is like this, but there are actually paired end techniques (the only one coming to mind right now is scATAC-Seq, although that is technically not transcriptomics)" From Enrique Sapena Ventura (a Data wrangler from HCA).

 
- Multimapping parameter (e.g. 200, 100, etc, does it saturate?)
- Reference genome
  - no ALTs (we would count e.g. one HERV as different HERVs if i's in the intron of e.g. an MHC gene and it's got multiple ALTs
  - Check [this post](https://www.biostars.org/p/342482/) in Biostars about human reference genome 
  - Consider using [Refgenie](http://refgenie.databio.org/en/latest/)

- How should we parse the barcodes for TELESCOPE?


### Aligners ###

- STARsolo gives us a multimapping BAM aligned to reference genome (not transcriptome), with UMIs and BCs in the read name or tags
- Can STARsolo find the whitelist when we don't provide the whitelist?
- Check STARsolo BAM reads aligning to multiple locations but deemed "not multi gene"

- Hisat as an alternative


## To do ##

- Assess statistical performance (simulated data?)
  - Eventually, the Snakemake report utility can be useful here (from a computational standpoint how much time it tooke, cores, timestamps, etc)
  - Parameter space exploration
- Demonstrate its biological relevance (find a good dataset)
  - "is there a particular set of data that analyzing with scTELESCOPE would advance knowledge? (importance of TE expression at the single-cell level)"
  - Whichever data we choose, there should be bulk RNA-seq to compare
  - People have mouse ESCs as proof of concept

- How are good computational papers structured?
  - which journal? model paper sections


## September scTELESCOPE codeathon  ##

- Input:
  - Code to run and test
  - Datasets

- Output:
  - Documentation
  - Tutorial
  - Demo
  - Manuscript


## Big single-cell projects ##

- Human Cell Atlas
- 10x datasets



