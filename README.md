# Overview

This is an example of analysis that can be run on data that is generated from processing with dada2. It assumes that processing has been performed and a counts table has been produced that contains amplicon sequence variants (rows) and samples (columns) with each element in the matrix being the count. We include these data in the hope that the analysis can be reproduced and the code can be used for anyone performing similar analyses. An example report that was built using these scripts and data can be found [here](https://www.kennedy.ox.ac.uk/files/research/advanced_data_analysis.html).

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

# Configuration

In order to run the analysis it is required that you provide paths to the scripts and data that are used. Scripts that are used come from various repositories - they are mainly wrappers for quite generic functions but need to be present for this particular analysis to run. First download or clone the following repositories:

[MIGTranscriptomeExplorer](https://github.com/nickilott/MIGTranscriptomeExplorer)

[NGSKit](https://github.com/nickilott/NGSKit)

[AmpSeqKit](https://github.com/nickilott/AmpSeqKit)

# Running the example data

The data/ directory in this repository contains the count data (ASV counts) and the metadata that maps sample identifiers to variables of interest. These data come from publically available data for [this study](https://www.nature.com/articles/s41522-018-0059-0). The data are 16S rRNA amplicon sequencing data (V4 region sequenced on the Illumina MiSeq) from wild-type mice and MMP-9 deficient mice in either untreated or DSS treatemd conditions (i.e. inflammatory bowel disease model. Please see the original article for more details. Sequence data were processed using dada2 implemented in pipeline_dada2.py from [here](https://github.com/nickilott/NGSKit).

The data look like the following:

## Counts matrix

|sequence                                                                                             |stool-2DSS__10  stool-2DSS__11  stool-2DSS__12  stool-2DSS__13 |
|-----------------------------------------------------------------------------------------------------|---------------|---------------|---------------|---------------|
|ASV1:p__Bacteroidetes;c__Bacteroidia;o__Bacteroidales;f__Porphyromonadaceae;g__Barnesiella;s__NA     |    7278       |      16       |       0       |     756       |
|ASV2:p__Firmicutes;c__Clostridia;o__Clostridiales;f__Lachnospiraceae;g__Clostridium XlVa;s__NA       |    3669       |      0        |       0       |     0         |
|ASV3:p__Bacteroidetes;c__Bacteroidia;o__Bacteroidales;f__Prevotellaceae;g__Alloprevotella;s__NA      |    3437       |      0        |       0       |     829       |
|ASV4:p__Bacteroidetes;c__Bacteroidia;o__Bacteroidales;f__Prevotellaceae;g__Prevotella;s__NA          |    1622       |      0        |       0       |     191       |
|ASV5:p__Bacteroidetes;c__Bacteroidia;o__Bacteroidales;f__Porphyromonadaceae;g__Barnesiella;s__NA     |    1517       |      110      |       0       |     461       |




## Metadata