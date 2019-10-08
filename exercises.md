---
layout: default
title: Exercises - scRNAseq course
---

# Welcome to NBIS scRNA-seq tutorials

Here we provide short tutorials on the different steps of scRNAseq analysis using either of the 3 most commonly used scRNAseq analysis pipelines, Seurat, Scran and Scanpy. 

<br/>

### Installations

We have conda recipies for all R packages in one file and for the Scanpy tutorial in another. If you have never worked with conda before, please read the [conda instructions](conda_instructions.md).

OBS! Need to fix some paths in instruction.
Also info on Docker?

<br/>

### Dataset

We will run all tutorials with a set of 3 PBMC 10x datasets from the 10X Genomics website, with different types of library preps.

These can be fetched using commands:

      mkdir data  
      cd data
      curl -O http://cf.10xgenomics.com/samples/cell-exp/3.0.0/pbmc_1k_v2/pbmc_1k_v2_filtered_feature_bc_matrix.h5
      curl -O http://cf.10xgenomics.com/samples/cell-exp/3.0.0/pbmc_1k_v3/pbmc_1k_v3_filtered_feature_bc_matrix.h5
      curl -O http://cf.10xgenomics.com/samples/cell-exp/3.0.0/pbmc_1k_protein_v3/pbmc_1k_protein_v3_filtered_feature_bc_matrix.h5

All code is written so that you stand in the folder where the scripts are when you run the code and fetch data from the data folder with path `../data/` and all output files goes into folder `../write/lab_name/` where `lab_name` can be either of `scran`, `scanpy` or `seurat`.

So also create the folder 'write' and subfolders for the lab you are planning to run.

   	cd ..
	mkdir write
	mkdir write/seurat
	mkdir write/scran
	mkdir write/scanpy	

<br/>

## Tutorials

Here are the tutorials using [Seurat](https://satijalab.org/seurat/), [Scran](https://bioconductor.org/packages/release/bioc/html/scran.html) or [Scanpy](https://scanpy.readthedocs.io/en/stable/). It is up to you which one you want to try out, if you finish quickly, you may have time to run several of them.

In principle we perform the same steps with all 3 pipelines, but there are some small differences as all different methods are not implemented in all the pipelines. 

| Tutorial | Seurat | Scran | Scanpy |
| -------- | ------ | ----- | ------ |
| QC | [Seurat_qc](labs/compiled/seurat/seurat_01_qc_compiled.md) | [Scater_qc](labs/compiled/scater/scater_01_qc_compiled.md) | [ScanPY_qc](labs/scanpy/qc_3pbmc.ipynb) |
| Dimensionality reduction | [Seurat_dr](labs/compiled/seurat/seurat_02_dim_reduction_compiled.md) | [Scater_dr](labs/compiled/scater/scater_02_dim_reduction_compiled.md) | [ScanPY_dr](labs/scanpy/dim_reduction.ipynb) |
| Data integration | [Seurat_integr](labs/compiled/seurat/seurat_03_integration_compiled.md) | [Scater_integr](labs/compiled/scater/scater_03_integration_compiled.md) | [ScanPY_integr](labs/scanpy/batch_correction_mnn.ipynb) |
| Clustering | [Seurat_clust](labs/compiled/seurat/lab_seurat.html) | [Scater_clust](labs/compiled/scater/lab_scran.html) | [ScanPY_clust](labs/scanpy/qc_3pbmc.ipynb) |
| Differential expression | [Seurat_dge](labs/compiled/seurat/lab_seurat.html) | [Scater_dge](labs/compiled/scater/lab_scran.html) | [ScanPY_dge](labs/scanpy/qc_3pbmc.ipynb) |
| Trajectory inference | [Monocle_ti](labs/compiled/monocle/monocle.html) | [Slingshot_ti](labs/compiled/slingshot/slingshot.html) | [PAGA_ti](labs/paga/paga.ipynb) |

<br/>

### FAQ

As you run into problems, we will try to fill in the [FAQ](labs/FAQ) with common questions.

<br/>

## Additional bonus exercises


| Name (link) | Description |
| ----------- | ----------- |
| [Read-Pipeline](labs/Pipeline_exercise) | Snakemake pipeline for processing SmartSeq2 data, mapping reads, QC and expression estimates|
| [biomaRt](labs/biomart) | For those not familiar with working with biomaRt, we suggest that you have a look at this example code for how to convert between different formats using biomaRt|
| [PCA, tSNE and clustering](labs/PCA_and_clustering) | Basic PCA, tSNE and clustering using base R on mouse embryonic development data. | 
| [KNN-graphs](labs/igraph) | Construction of graphs from cell-cell similiarities using igraph|
| [Estimating Batch-Effects](https://bitbucket.org/scilifelab-lts/scrnaseq-labs/src/a228442debe7f8eff28cfdba875349025db9b7a3/batch_analysis.md?fileviewer=file-view-default) | A tutorial for estimating genome-wide and individual genes batch-effects |
| [Normalization Comparison](labs/norm_analysis_v2) | A tutorial for comparison scRNAseq and bulk RNAseq normalisation strategies. | [Tutorial for Normalisation](labs/norm_analysis_v2)  |
| [SC3 package](labs/sc3_R35) | Tutorial with the SC3 consensus clustering package |
| [Trajectory with Monocle2](labs/monocle_analysis) | A tutorial with mouse embryonic data using the Monocle package for pseudotime analysis |
| [Differential expression_2](labs/Differential_gene_expression) [Differential expression_2](labs/Differential_gene_expression) | OBS! This old tutorial uses Seurat v2! For this tutorial we have included several different methods for differential expression tests on single cell data, including SCDE, MAST, SC3 and Seurat. The exercise has been split into 2 parts with evaluation of all results in the second part |
| [UPPMAX Sbatch](labs/sbatchScript) | One example of a sbatch script |
| [Pagoda](labs/pagoda_ilc) | Pagoda patway wPCA for clustering of cells. OBS! several steps in this tutorial takes hours to run if you work with your own dataset, a good suggestion is to start with the first steps, knn.error.model, pagoda.varnorm and pagoda.pathway.wPCA and let it run while working on other tutorials. You can also run it with more than one core to speed things up |

<br/>


#### Pipeline for mapping reads, QC and expression estimates

Snakemake pipeline for processing SmartSeq2 data.

* [Pipeline tutorial](labs/Pipeline_exercise) 

#### Biomart - Convert gene names and fetch annotation

For those not familiar with working with biomaRt, we suggest that you have a look at this example code for how to convert between different formats using biomaRt. 
* [Tutorial for biomaRt](labs/biomart) 

#### PCA, tSNE and clustering

Basic PCA, tSNE and clustering using base R on mouse embryonic development data.

* [Tutorial for PCA and clustering](labs/PCA_and_clustering)


#### Constructing knn graphs

Construction of graphs from cell-cell similiarities using igraph.  

* [Tutorial for KNN graphs](labs/igraph)		  


#### Estimating Batch-Effects

A tutorial for estimating genome-wide and individual genes batch-effects.

* [Tutorial for Batch-Effects](https://bitbucket.org/scilifelab-lts/scrnaseq-labs/src/a228442debe7f8eff28cfdba875349025db9b7a3/batch_analysis.md?fileviewer=file-view-default)

#### Comparing Normalization Methods

A tutorial for comparison scRNAseq and bulk RNAseq normalization strategies.

* [Tutorial for Normalization](labs/norm_analysis_v2)

#### SC3 package

Tutorial with the SC3 consensus clustering package

* [Tutorial for SC3](labs/sc3_R35)

#### Pagoda package

Pagoda patway wPCA for clustering of cells. OBS! several steps in this tutorial takes hours to run if you work with your own dataset, a good suggestion is to start with the first steps, knn.error.model, pagoda.varnorm and pagoda.pathway.wPCA and let it run while working on other tutorials. You can also run it with more than one core to speed things up.
 
* [Tutorial for Pagoda](labs/pagoda_ilc)

#### Differential expression

OBS! This old tutorial uses Seurat v2! For this tutorial we have included several different methods for differential expression tests on single cell data, including SCDE, MAST, SC3 and Seurat. The exercise has been split into 2 parts with evaluation of all results in the second part. 

* [Tutorial for DE detection 1](labs/Differential_gene_expression)
* [Tutorial for DE detection 2](labs/Differential_gene_expression_part2)

#### Monocle Pseudotime analysis

A tutorial with mouse embryonic data using the Monocle package for pseudotime analysis.

* [Tutorial for Monocle](labs/monocle_analysis)   

#### UPPMAX Sbatch
 
One example of a sbatch script
 
* [sbatch scripts](labs/sbatchScript)   
 
#### Caveat

We will try to keep these tutorials up to date. If you find any errors or things that you think should be updated please contact Asa (asa.bjorklund@scilifelab.se) 
  		
