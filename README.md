# Overview

This is an example of analysis that can be run on data that is generated from processing with dada2. It assumes that processing has been performed and a counts table has been produced that contains amplicon sequence variants (rows) and samples (columns) with each element in the matrix being the count. We include these data in the hope that the analysis can be reproduced and the code can be used for anyone performing similar analyses. An example report that was built using these scripts and data can be found [here](https://www.kennedy.ox.ac.uk/files/research/advanced_data_analysis.html).

The analysis on example data can be run by rendering the ocms_example_16SrRNA.Rmd file in the Rmd/ folder. Dependencies and steps required to run these analyses are detailed below. The idea behind this repository is that much of the code in Rmd/ocms_example_16SrRNA.Rmd could be re-used for analyses in similar datasets.

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

# Configuration

In order to run the analysis it is required that you provide paths to the scripts and data that are used. Scripts that are used come from various repositories - they are mainly wrappers for quite generic functions but need to be present for this particular analysis to run. Firts download or clone the following repositories:

[MIGTranscriptomeExplorer](https://github.com/nickilott/MIGTranscriptomeExplorer)
[NGSKit](https://github.com/nickilott/NGSKit)
[AmpSeqKit](https://github.com/nickilott/AmpSeqKit)
