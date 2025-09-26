# Ciprofloxacin resistance in _Klebsiella pneumoniae_

This repository houses data and R code for the paper: ["Ciprofloxacin resistance in _Klebsiella pneumoniae_: phenotype prediction from genotype and global distribution of resistance determinants"](https://doi.org/10.1101/2025.09.24.678318), by the [KlebNET-GSP AMR Genotype-Phenotype Group](https://klebnet.org/amrgenopheno/).

The primary input data is in supplementary Tables S2 and S3 of the paper, included here as `tables/TableS2_genotypes.tsv` (genotype data) and `tables/TableS3_phenotypes_metadata.tsv` (susceptibility phenotypes and metadata).

Each `.Rmd` file contains R code that uses these data files to generate figures, tables, or summary statistics presented in the paper. Executing an `.Rmd` file using knitR generates a corresponding `.html` file, where you can view the code itself and the outputs of each code block. Figures and tables shown in the paper are generated using these `.Rmd` files, and are written to the directories `tables/` and `figures/`.

Public data downloaded from [Pathogenwatch](https://pathogen.watch/) via [this site](https://cgps.gitbook.io/pathogenwatch/public-data-downloads), and corresponding code, is in the `Pathogenwatch/` directory. Output figures are written to the main `figures/` directory.

## Kleborate and Pathogenwatch

The ciprofloxacin resistance predictor can be used via: 

- [Kleborate v3.2.4](https://github.com/klebgenomics/Kleborate) (command line tool) 
- [Pathogenwatch v23.4.4](https://pathogen.watch/) (web-based tool)

Information about the four columns used to report ciprofloxacin resistance prediction results can be found [here.](https://kleborate.readthedocs.io/en/latest/kpsc_modules.html#ciprofloxacin-resistance-prediction)

## Citations
If you use the code in this repository, please cite this repository and its DOI: Tsang et al, 2025. "Ciprofloxacin resistance in _Klebsiella pneumoniae_", https://github.com/klebgenomics/cipropaper (DOI:10.5281/zenodo.17193872).

If you use any data, figures or tables from this repository, please cite the paper: "Ciprofloxacin resistance in Klebsiella pneumoniae: phenotype prediction from genotype and global distribution of resistance determinants", BioRxiv 2025 (DOI: [10.1101/2025.09.24.678318](https://doi.org/10.1101/2025.09.24.678318)).

If you use Kleborate to analyse your own data and report the ciprofloxacin predictions, please cite the paper: Tsang et al, "Ciprofloxacin resistance in Klebsiella pneumoniae: phenotype prediction from genotype and global distribution of resistance determinants", BioRxiv 2025 (DOI: [10.1101/2025.09.24.678318](https://doi.org/10.1101/2025.09.24.678318)) as well as the [primary Kleborate paper](https://www.nature.com/articles/s41467-021-24448-3).

[![DOI](https://zenodo.org/badge/860325627.svg)](https://doi.org/10.5281/zenodo.17193872)
