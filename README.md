# Overview

This is an example of analysis that can be run on data that is generated from processing with dada2. It assumes that processing has been performed and a counts table has been produced that contains amplicon sequence variants (rows) and samples (columns) with each element in the matrix being the count. We include these data in the hope that the analysis can be reproduced and the code can be used for anyone performing similar analyses. An example report that was built using similar scripts with these data can be found [here](https://www.kennedy.ox.ac.uk/files/research/advanced_data_analysis.html).

The analysis on example data can be run by rendering the ocms_example_16SrRNA.Rmd file in the Rmd/ folder. Dependencies and steps required to run these analyses are detailed below. The idea behind this repository is that much of the code in Rmd/ocms_example_16SrRNA.Rmd could be re-used for analyses in similar datasets.

Please take into account that this is an example and we do not go through checking of the data in any depth. Rather, this is a simplified version of an analysis that can be performed to look for differential features between groups after thorough exploratory analysis.

# Dependencies

There are no checks that are performed in terms of installed dependencies so please ensure that the following packages are installed if you want to re-run the analysis in the example or run the code on your own data.

| **R package**   |
|-----------------|
| knitr           |
| gridExtra       |
| phyloseq        |
| ggplot2         |
| data.table      |
| vegan           |
| pheatmap        |
| RMarkdown       |
| DESeq2          |
| reshape         |
| RColorBrewer    |
| dplyr           |
| gplots          |

# Scripts

In order to run the analysis it is required that you provide paths to the scripts and data that are used. Scripts that are used come from various repositories - they are mainly wrappers for quite generic functions but need to be present for this particular analysis to run. First download or clone the following repositories:

[MIGTranscriptomeExplorer](https://github.com/nickilott/MIGTranscriptomeExplorer)

[NGSKit](https://github.com/nickilott/NGSKit)

[AmpSeqKit](https://github.com/nickilott/AmpSeqKit)

# Configuration

Paths to the repositories outlined in above should be specified in the ocms_example_16SrRNA.config.R file before running the analysis.

# Running the example data

The data/ directory in this repository contains the count data (ASV counts) and the metadata that maps sample identifiers to variables of interest. These data come from publically available data for [this study](https://www.nature.com/articles/s41522-018-0059-0). The data are 16S rRNA amplicon sequencing data (V4 region sequenced on the Illumina MiSeq) from wild-type mice and MMP-9 deficient mice in either untreated or DSS treatemd conditions (i.e. inflammatory bowel disease model. Please see the original article for more details. Sequence data were processed using dada2 implemented in pipeline_dada2.py from [here](https://github.com/nickilott/NGSKit).

In order to run the analysis, create a new working directory where you want to run the analysis. Copy the following data files into this directory:

* data/metadata.tsv
* data/asvs.tsv
* R/ocms_example_16SrRNA.config.R
* Rmd/ocms_example_16SrRNA.Rmd

Once these are copied, open R or RStudio and edit the ocms_example_16SrRNA.config.R in the working directory so that it points to where you have downloaded these repositories e.g.

```
######################################################
######################################################
# Configuration file for ocms_example_16SrRNA.Rmd
######################################################
######################################################

# R scripts - these can be cloned from github and
# functions in them are required for running the example

AmpSeqKit.dir="<path-to-where-downloaded>/AmpSeqKit"
NGSKit.dir="<path-to-where-downloaded>/NGSKit"
MIGTranscriptomeExplorer.dir="<path-to-where-downloaded>/MIGTranscriptomeExplorer"

# Data

# ASV counts table
asv.counts="asvs.tsv"

# metadata
metadata="metadata.tsv"

```

Once this is done it should be as simple as firing up R/RStudio and running:

```
rmarkdown::render("ocms_example_16SrRNA.Rmd", output_format="html_document")
```

This will produce an html report that contains the analysis results and the code that was run to produce the results. This should provide code snippets and such for use in your own data analysis. If you want to run the steps one by one then the html is already build at html/ocms_example_16SrRNA.html. There is also a pdf, pdf/ocms_example_16SrRNA.pdf that is the analysis guide.

