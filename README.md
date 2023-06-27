# GEO Database Mining - Comprehensive Bioinformatics Expression Matrix Analysis Repository Overview

## Main Project Code Folders:

- GSE42872_main: Demonstrates the standard six steps for mining the GEO database.
- GSE11121_survival: Demonstrates batch survival analysis based on gene expression grouping.

## Six Task Project Folders:

### task1-check-specific-genes:
Demonstrates the performance of specific genes of interest across multiple GSE datasets.

### task2-lncRNA-mRNA-network:
Demonstrates how to construct a network.

### task3-multiple-groups:
Demonstrates downstream analysis when sample grouping information is complex.

### task4-NPC:
Demonstrates the standard six steps for mining the GEO database, similar to GSE42872_main.

### task5-dynamic-network-biomarker:
Demonstrates a novel algorithm beyond the standard six steps for GEO database mining shown in GSE42872_main.

### task6-GEO-TCGA:
Demonstrates how to integrate the TCGA database.

## Two Additional Supplementary Project Folders:

### airway_RNAseq:
Demonstrates the analysis of expression matrices obtained from RNA-seq, highlighting similarities and differences compared to traditional microarray expression matrices.

### breast_cancer_meta-analysis:
Demonstrates how to perform meta-analysis.

## Below is a code snippet from the main code folder, GSE42872_main:

```R
# Step 1: Download Data
# Data is the soul!

# It may not be easy to download data in China, so I have also uploaded the file GSE42872_raw_exprSet.Rdata, which you can load directly.

if(F) {
  library(GEOquery)
  gset <- getGEO('GSE42872', destdir=".",
                 AnnotGPL = F,
                 getGPL = F)
  save(gset, 'GSE42872.gset.Rdata')
}

load('GSE42872_eSet.Rdata')
b <- eSet[[1]]  # Please note that some GSE datasets have multiple platforms. Pay attention to the selection.
raw_exprSet <- exprs(b) 
group_list <- c(rep('control', 3), rep('case', 3))
save(raw_exprSet, group_list,
     file = 'GSE42872_raw_exprSet.Rdata')

# Step 2: Check the Expression Matrix
# High-quality data is crucial!

# I filtered the probes based on microarray annotation, and how I checked the group information for different samples in each experiment.
# This includes PCA and Cluster figures.
