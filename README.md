# The host cell's ER proteostasis network profoundly shapes the protein sequence space accessible to HIV envelope

Deep mutational scanning analysis for "The host cell's ER proteostasis network profoundly shapes the protein sequence space accessible to HIV Envelope"

This repository is for the project by Jimin Yoon, Emmanuel Nekongo, and Matthew Shoulders (https://shoulderslab.mit.edu). This project analyzes the impact of host ER proteostasis network on the mutational tolerance of human immunodeficiency virus (HIV) envelope (Env). The analysis primarily uses [dms_tools2](https://jbloomlab.github.io/dms_tools2/index.html).

## Analysis

### Calculating codon counts from FASTQ files

This analysis is performed by analysis_notebook.ipynb. The 
The analysis requires the following input data.

 * The FASTQ files from deep mutational scanning. The FASTQ files can be downloaded from the Sequence Read Archive under SRA project SRP314168 and BioProject PRJNA720817

 * The wildtype Env sequence for the LAI strain used in the experiment. The seqeucne file (LAI_Env_reference.fa) can be found in the main directory.

