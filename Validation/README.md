# Ciprofloxacin resistance paper - Validation instructions

## Run Kleborate v3 (cipro_prediction branch: https://github.com/klebgenomics/Kleborate/tree/cipro_prediction)

Make sure you have all dependencies installed (https://kleborate.readthedocs.io/en/latest/Installation.html)

- A great option is to create a conda environment:

```
conda create -n klebsiella_analysis -c bioconda python=3.9 minimap2 mash -y
conda activate klebsiella_analysis
```

As the ciprofloxacin classifier is on a separate git branch, please do the following: 

```
git clone https://github.com/klebgenomics/Kleborate.git
cd Kleborate
git checkout cipro_prediction
python /path_to/Kleborate/kleborate-runner.py -a /path_to_assemblies/*.fasta -o /path_to_output/ -p kpsc --trim_headers
```

The expected output is a txt file `klebsiella_pneumo_complex_output.txt` in the output folder indicated in the command above. 

This file has all Kleborate v3 columns with three additional columns at the end of the text file named `cipro_prediction`, `cipro_prediction_group`, `cipro_prediction_support`.


## Share outputs

### Preferred option: 

Send us:
1. Kleborate v3 (cipro_prediction branch) columns: **strain, species, cipro_prediction, cipro_prediction_group**
2. Antibiogram data: MIC / disk diffusion measurements for each strain

### Second best option:

If it is not possible to share sample-level info, run the R code (CipPaper_Validation.Rmd)

Replace **klebsiella_pneumo_complex_output_v3_test.txt** and **TableS2_phenotypes_metadata.tsv** with the names of your kleborate and antibiogram file, respectively. 

Ensure that the kleborate and antibiogram file are in the same directory as the CipPaper_Validation.Rmd file. 

#### CipPaper_Validation.Rmd Details

- The antibiogram file should be in the in the same format as the NCBI's BioSample Antibiogram Format (see Download antibiogram template: https://www.ncbi.nlm.nih.gov/biosample/docs/antibiogram/)
The strain identifier column header is `strain`. If your antibiogram file is **not** in this format, please contact Kara (kara.tsang@lshtm.ac.uk) with the headers in your antibiogram file and a sample entry so that a CipPaper_Validation.Rmd file specific to your antibiogram data can be sent to you.

- CipPaper_Validation.Rmd assumes that you have both MIC and disk diffusion data - if you only have one form of data you can delete the plotting code under each relevant section ** MIC distribution ** or ** DD distribution **

- CipPaper_Validation.Rmd filters for only ***Klebsiella pneumoniae*** - if you have other KpSC species, please change the species in the following part of the code: 

```
cipro_antibiogram <- cipro_antibiogram %>% filter(species=="Klebsiella pneumoniae")
```

Before re-rerunning CipPaper_Validation.Rmd again for the next species, please ensure that previous outputs (in the ValidationOutput folder) are renamed so that they are not overwritten.


#### CipPaper_Validation.Rmd Expected Outputs

Expected outputs can be visualized by viewing the CipPaper_Validation.html file. 

- The expected output of running CipPaper_Validation.Rmd is a folder called ValidationOutput with the following files:

  - Prediction_Pheno_summary.csv: reports numbers for S/I/R phenotypes vs. S/I/R predictions and phenotype groups. Includes S/I/R phenotypes as column headers and S/I/R predictions + cipro_prediction_groups as row headers.

  - StackedBar_PredGroup_SIR.png / StackedBar_PredGroup_SIR.pdf: stacked bar plot showing S/I/R phenotype vs. cipro_prediction_group

  - MIC_PredRIS.png / MIC_PredGroup.pdf - MIC distribution vs. S/I/R predictions (only expected if you have MIC data)
  - MIC_PredGroup.png / MIC_PredGroup.pdf - MIC distribution vs. cipro_prediction_group (only expected if you have MIC data)

  - DD_PredRIS.png / DD_PredGroup.pdf - Disk diffusion distribution vs. S/I/R predictions (only expected if you have DD data)
  - DD_PredGroup.png / DD_PredGroup.pdf - Disk diffusion distribution vs. cipro_prediction_group (only expected if you have DD data)
  
### Third best option:
If above options are not possible, the **minimum** we require is for you to independently to cross-tabulate the cipro_prediction_group column vs. S/I/R calls.