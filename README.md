# diricore

There are 3 main scripts:
1. `subsequence_analysis.sh`
2. `rpf_density_analysis.sh`
3. `plot_rpf_transcript_distribution.sh`

To run them, the paths specified in the scripts have to be changed to the correct ones.

## Input files
It is required to have the following input files:

1. contrasts `rpf_density_contrasts.tsv`

Contrasts

```
S3_Tumor1_HA    S1_Spleen_HA    #cc00cc
S3_Tumor1_HA    S2_Spleen2_HA   #668cff
S4_Tumor2_HA    S1_Spleen_HA    #ff6666
S4_Tumor2_HA    S2_Spleen2_HA   #00cc99
S5_Tumor3_HA    S1_Spleen_HA    #262626
S5_Tumor3_HA    S2_Spleen2_HA   #b366ff
```

Where `S3_Tumor1_HA` is a treated sample, `S1_Spleen_HA` is a control sample, and `#cc00cc` is the color of the contrast

2. sample names: `rpf_density_samplenames.tsv`

```
S1_Spleen_HA    S1_Spleen_HA    #cc00cc
S2_Spleen2_HA   S2_Spleen2_HA   #668cff
S3_Tumor1_HA    S3_Tumor1_HA    #ff6666
S4_Tumor2_HA    S4_Tumor2_HA    #00cc99
S5_Tumor3_HA    S5_Tumor3_HA    #262626
```

3. Bam files - diricore works with the aligned reads. 

## Static files

Diricore supports 3 types of genomes:
1. Human (hg19)
2. Mouse (mm10)
3. Yeast

# Workflow
0. THE most important step: change all the directories in the script. 
1. Align raw data with any aligner of choice, e.g. STAR
  * For human, use this genome version: https://www.gencodegenes.org/human/release_19.html
  * For mouse, use this genome version: https://www.ensembl.org/Mus_musculus/Info/Index 
2. Run RPF density analysis: `rpf_density_analysis.sh 20252 mm10 25 all_unique`
3. Run Subsequence analysis: `subsequence_analysis.sh 20252 mm10 25 all_unique`
4. After the RPF density analysis is done, plot transcript distribution: `plot_rpf_transcript_distribution.sh 20252 mm9 25 all_unique`
