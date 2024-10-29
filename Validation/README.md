# Ciprofloxacin resistance paper - Validation instructions

## Run Kleborate v3 (cipro_prediction branch: https://github.com/klebgenomics/Kleborate/tree/cipro_prediction)
```
git clone https://github.com/klebgenomics/Kleborate.git
cd Kleborate
git checkout cipro_prediction
python /path_to/Kleborate/kleborate-runner.py -a /path_to_assemblies/*.fasta -o /path_to_output/kleborate_v3_cipropred -p kpsc --trim_headers
```

## Share outputs

### Preferred option: 

Send us:
1. Kleborate v3 (cipro_prediction branch) columns: **strain, species, cipro_prediction, cipro_prediction_group**
2. Antibiogram data: MIC / disk diffusion measurements and S/I/R interpretation for each strain

### Second best option:

If it is not possible to share sample-level info, run the R code (CipPaper_Validation.Rmd)

Replace **klebsiella_pneumo_complex_output_v3_test.txt** and **TableS2_phenotypes_metadata.tsv** with the names of your kleborate and antibiogram file, respectively. 

Ensure that the kleborate and antibiogram file are in the same directory as the CipPaper_Validation.Rmd file. 

#### Assumptions

- The antibiogram file should be in the in the same format as the NCBI's BioSample Antibiogram Format (see Download antibiogram template: https://www.ncbi.nlm.nih.gov/biosample/docs/antibiogram/)
If your antibiogram file is **not** in this format, please contact Kara (kara.tsang@lshtm.ac.uk).

- CipPaper_Validation.Rmd assumes that you have both MIC and disk diffusion data - if you only have one form of data you can delete the plotting code under each relevant section ** MIC distribution ** or ** DD distribution **

- The CipPaper_Validation.Rmd filters for only ***Klebsiella pneumoniae*** - if you have other KpSC species, please change the species in the following part of the code: 

```
cipro_antibiogram <- cipro_antibiogram %>% filter(species=="Klebsiella pneumoniae")
```

Before re-rerunning CipPaper_Validation.Rmd for the next species, please ensure that previous outputs (in the ValidationOutput folder) are renamed so that they are not overwritten.

Send us: ValidationOutput folder

### Third best option:
If above options are not possible, the **minimum** we require is to cross-tabulate the cipro_prediction_group column vs S/I/R calls.