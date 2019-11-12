# Overview

This is an example of analysis that can be done on data that is generated from processing with dada2. It assumes that processing has been performed and a counts table has been produced that contains amplicon sequence variants (rows) and samples (columns) with wach element in the matrix being the count. We include these data in the hope that the analysis can be reproduced and the code can be used for anyone performing similar analyses.

## Dependencies

There are no checks that are performed in terms of installed dependencies so please ensure that the following packages are installed if you want to re-run the analysis in the example or run the code on your own data.

| **R package** |
-----------------
|:knitr:        |
|:gridExtra:    |
|:phyloseq:     |
|:ggplot2:      |
|:data.table:   |
|:vegan:        |
|:pheatmap:     |
