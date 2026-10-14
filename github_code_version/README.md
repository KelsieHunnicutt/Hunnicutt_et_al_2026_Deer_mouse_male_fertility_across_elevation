## Description
This code accompanies the manuscript "Reduced baseline male fertility and increased sensitivity to hypoxic stress in high-elevation deer mice" by Hunnicutt et al. 2026.

## Abstract
Extreme environments like high elevation impose chronic challenges to endothermic animals who must sustain metabolic demand despite reduced oxygen availability. Male reproduction is a tightly regulated physiological system, and hypoxia exposure has negative but transient effects on male reproductive output in diverse mammal species not adapted to high-elevation. Little is known about whether high elevation populations adapt to the detrimental effects of hypoxia on male reproductive physiology. Here, we use high- and low-elevation populations of deer mice (Peromyscus maniculatus) and a lowland congener, P. leucopus, to test how male reproductive phenotypes have diverged across populations and in response to hypoxia exposure across acute, intermediate, and chronic timescales. We complement these phenotypic assays with bulk RNA sequencing of testes to assess the testis-specific response to hypoxia. Contrary to expectations, hypoxia exposure had a negligible effect on low-elevation strains, while highland mice had both lower baseline fertility and heightened sensitivity to hypoxic stress including complete absence of mature sperm. Gene expression patterns indicate that hypoxia exposure dramatically reorganizes testes architecture in highland mice, consistent with testicular regression similar to that observed in seasonally breeding mammals. We hypothesize that this increased sensitivity of male reproductive physiology in highlanders reflects a life history trade-off, allowing energy reallocation between reproduction, survival, and thermogenesis in response to stress in extreme environments. 

## Instructions
This repository consists of an /exported_figures/, /exported_files/, /reference_files/, and /RNAseq_count_files/, the three main scripts, and this ReadME.

The three main scripts are:

High_elevation_male_fertility_for_github.md
Deer_mouse_testes_hypoxia_phenotypes_script.Rmd
Deer_mouse_testes_hypoxia_RNASeq_star.Rmd

They are accompianed by their knitted Rmarkdown files:

Deer_mouse_testes_hypoxia_phenotypes_script.html
Deer_mouse_testes_hypoxia_RNASeq_star.html

These scripts should be run in the above listed order. The first script processes the raw fastq data and the two Rmarkdown scripts process the phenotype data and the RNAseq data respectively.

The Rmd scripts expect the user's working directory to contain the /exported_figures/, /exported_files/, /reference_files/, and /RNAseq_count_files/ folders. R v4.5.0 and RStudio v2025.05.1+513 were used for these analyses.

In addition to the provided files, users will need to download the NCBI RefSeq annotation for P. maniculatus (GCF_049852395.1_HU_Pman_BW_mat_3.1_annotation.gtf) and the single cell expression matrices for ST1-ST8 from Green et al. 2018 (https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE112393).

## Authors
- Kelsie E. Hunnicutt (0000-0002-9674-0630)
- Emma S. Glenn (0009-0000-0789-9918)
- Joe C. Perry (0009-0003-4253-3120)
- Madison Q. Tatro (0009-0005-5625-1065)
- Lacey K. Conrad (0009-0006-6988-6219)
- Makenna Y. Juergens (0009-0005-6366-5979)
- Kathryn Wilsterman (0000-0001-7262-9754)
- Benjamin M. Skinner (0000-0002-7152-1167)
- Erica L. Larson (0000-0003-3006-645X)
- Jonathan P. Velotta (0000-0002-3100-9951)

## Affiliations
- Department of Biological Sciences, University of Denver, Denver, CO 80210, USA
- Department of Biology, Stanford University, Stanford, CA 94305, USA
- School of Life Sciences, University of Essex, Colchester CO4 3SQ, UK
- Department of Biology, Colorado State University, Fort Collins, CO 80523, USA

## Funding
- NSF GRFP (DGE-2034612 to KEH)
- NIH NIGMS (F32GM163371 to KEH)
- NIH NIGMS (R35GM147459 to JVP)
- NSF DEB (2337629 to ELL)
- NIH NICHD (R01 HD114615 to KW)
- NSF IOS (2512875 to KW)
- Boettcher Foundation Webb-Waring Biomedical Research Award (KW)

## Data Files

### `exported_files/~$phenotype_statistical_models.xlsx`
### `exported_files/ensembl_mouse_to_deer_mouse_orthologs.csv`
File of ensembl mouse to deer mouse orthologs

### `reference_files/annotations/GCF_049852395.1_chromosome_list.csv`
Chromosome information for P. maniculatus assembly

###`reference_files/Green_GSE112393_samples/GSE112393_MergedAdultMouseST25_PerCellAttributes.txt`
Per-cell cell type attributes from Green et al. 2018

### `reference_files/KN_ME_mouse_records.csv`
University of Denver mouse colony info for the focal comparison

### `reference_files/Pero_stock_center_mouse_records.csv`
University of Denver mouse colony info for extended comparison mice from the Peromyscus stock center

### `reference_files/Peromyscus_acclimation_data_phenotypes_21Jul26.csv`
Male reproductive phenotyping data for the focal and extended comparisons

### `reference_files/schweizer_2019_catecholamine_genes.csv`
Previously identified set of catecholamine genes of interest from Schweizer et al. 2019

### `reference_files/strain_localities.csv`
Approximate collection locality info for all strains included in the manuscript

### `reference_files/Wilsterman_2023_PBS_outliers.csv`
List of previously described PBS outliers between highland and lowland deer mice from Wilsterman et al. 2023

### `reference_files/Wilsterman_colony_data/maleColonyRecords_Mar142026.csv`
Colony records from CSU repeated baseline fertility measurements

### `reference_files/Wilsterman_colony_data/READ.ME.xlsx`
README to accompany CSU colony records

## Other Files

### `Deer_mouse_testes_hypoxia_phenotypes_script.html`
Knitted Rmarkdown file to accompany Deer_mouse_testes_hypoxia_phenotypes_script.Rmd

### `Deer_mouse_testes_hypoxia_RNASeq_star.html`
Knitted Rmarkdown file to accompany Deer_mouse_testes_hypoxia_RNASeq_star.Rmd

### `exported_files/ExprTOM_testes-block.1.RData`
WGCNA Topological Overlap Matrix (TOM) as an RData file

### `exported_files/spermoxia_testes_Network.RData`
WGCNA network object as an RData file

### `High_elevation_male_fertility_for_github.md`
This file describes how raw fastq files were processed to count files with STAR (see methods)

### `reference_files/US_shape_object.rds`
US shape file object

## STAR produced counts files
### `RNAseq_count_files/K_G410B_C_T3_ReadsPerGene.out.tab`
### `RNAseq_count_files/K_G410B_D_T2_ReadsPerGene.out.tab`
### `RNAseq_count_files/K_G410B_E_T1_ReadsPerGene.out.tab`
### `RNAseq_count_files/K_G412C_C_T2_ReadsPerGene.out.tab`
### `RNAseq_count_files/K_G412C_D_T0_ReadsPerGene.out.tab`
### `RNAseq_count_files/K_G412C_H_T3_ReadsPerGene.out.tab`
### `RNAseq_count_files/K_G419A_C_T2_ReadsPerGene.out.tab`
### `RNAseq_count_files/K_G419A_D_T1_ReadsPerGene.out.tab`
### `RNAseq_count_files/K_G419A_E_T3_ReadsPerGene.out.tab`
### `RNAseq_count_files/K_G419B_A_T2_ReadsPerGene.out.tab`
### `RNAseq_count_files/K_G419B_C_T0_ReadsPerGene.out.tab`
### `RNAseq_count_files/K_G419B_O_T3_ReadsPerGene.out.tab`
### `RNAseq_count_files/K_G43A_G_T2_ReadsPerGene.out.tab`
### `RNAseq_count_files/K_G43A_I_T1R_ReadsPerGene.out.tab`
### `RNAseq_count_files/K_G45B_A_T3_ReadsPerGene.out.tab`
### `RNAseq_count_files/K_G45B_B_T0_ReadsPerGene.out.tab`
### `RNAseq_count_files/K_G45C_B_T1_ReadsPerGene.out.tab`
### `RNAseq_count_files/K_G45C_C_T0_ReadsPerGene.out.tab`
### `RNAseq_count_files/K_G47A_E_T0_ReadsPerGene.out.tab`
### `RNAseq_count_files/K_G47B_A_T0_ReadsPerGene.out.tab`
### `RNAseq_count_files/K_G47B_C_T1_ReadsPerGene.out.tab`
### `RNAseq_count_files/M_801_E_T0_ReadsPerGene.out.tab`
### `RNAseq_count_files/M_801_F_T0_ReadsPerGene.out.tab`
### `RNAseq_count_files/M_801_G_T2R_ReadsPerGene.out.tab`
### `RNAseq_count_files/M_801_H_T1_ReadsPerGene.out.tab`
### `RNAseq_count_files/M_803_A_T2_ReadsPerGene.out.tab`
### `RNAseq_count_files/M_803_B_T3_ReadsPerGene.out.tab`
### `RNAseq_count_files/M_803_C_T1_ReadsPerGene.out.tab`
### `RNAseq_count_files/M_805_A_T0_ReadsPerGene.out.tab`
### `RNAseq_count_files/M_805_B_T0_ReadsPerGene.out.tab`
### `RNAseq_count_files/M_805_J_T3_ReadsPerGene.out.tab`
### `RNAseq_count_files/M_805_K_T2_ReadsPerGene.out.tab`
### `RNAseq_count_files/M_805_L_T1_ReadsPerGene.out.tab`
### `RNAseq_count_files/M_807_F_T3_ReadsPerGene.out.tab`
### `RNAseq_count_files/M_809_B_T3_ReadsPerGene.out.tab`
### `RNAseq_count_files/M_810_D_T2_ReadsPerGene.out.tab`
### `RNAseq_count_files/M_812_E_T0R_ReadsPerGene.out.tab`
### `RNAseq_count_files/M_812_L_T3_ReadsPerGene.out.tab`
### `RNAseq_count_files/M_812_M_T0_ReadsPerGene.out.tab`

## Code
Scripts should be run in the following order:

1. **`High_elevation_male_fertility_for_github.md`**
2. **`Deer_mouse_testes_hypoxia_phenotypes_script.Rmd`**
3. **`Deer_mouse_testes_hypoxia_RNASeq_star.Rmd`**

## R Environment
**R version:** 4.5.0

| Package | Version |
| :------ | :------ |
| `betareg` | 3.2.6 |
| `Biobase` | 2.70.0 |
| `BiocParallel` | 1.44.0 |
| `biomaRt` | 2.64.0 |
| `car` | 3.1.5 |
| `circlize` | 0.4.18 |
| `ComplexHeatmap` | 2.24.1 |
| `corrplot` | 0.95 |
| `cowplot` | 1.2.0 |
| `data.table` | 1.18.6.1 |
| `dendextend` | 1.19.1 |
| `dplyr` | 1.2.1 |
| `edgeR` | 4.6.3 |
| `emmeans` | 2.0.4 |
| `faraway` | 1.0.9 |
| `FSA` | 0.10.1 |
| `geodata` | 0.6.9 |
| `ggbeeswarm` | 0.7.3 |
| `ggpattern` | 1.3.1 |
| `ggplot2` | 4.0.3 |
| `ggsignif` | 0.6.4 |
| `GO.db` | 3.21.0 |
| `gprofiler2` | 0.2.4 |
| `Hmisc` | 5.2.6 |
| `lme4` | 2.0.6 |
| `lmerTest` | 3.2.1 |
| `lubridate` | 1.9.5 |
| `MASS` | 7.3.66 |
| `MuSiC` | 1.0.0 |
| `nlme` | 3.1.170 |
| `openxlsx` | 4.2.8.1 |
| `org.Mm.eg.db` | 3.21.0 |
| `performance` | 0.17.1 |
| `purrr` | 1.2.2 |
| `raster` | 3.6.23 |
| `reshape2` | 1.4.5 |
| `rmapshaper` | 0.6.1 |
| `rnaturalearth` | 1.2.0 |
| `Rsubread` | 2.22.1 |
| `scales` | 1.4.0 |
| `sf` | 1.1.2 |
| `SingleCellExperiment` | 1.30.1 |
| `tidyr` | 1.3.2 |
| `tigris` | 2.2.1 |
| `variancePartition` | 1.38.1 |
| `vegan` | 2.7.6 |
| `VennDiagram` | 1.8.2 |
| `WGCNA` | 1.74 |

---
*README generated with READMEBuilder on 13 October 2026.*