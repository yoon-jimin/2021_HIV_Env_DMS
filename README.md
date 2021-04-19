# Deep mutational scanning of HIV Env in remodelled host cell ER proteostasis network

Deep mutational scanning analysis for "The host cell's ER proteostasis network profoundly shapes the protein sequence space accessible to HIV Envelope" (publication info goes here)

This repository is for the project by Jimin Yoon, Emmanuel Nekongo, and Matthew Shoulders (https://shoulderslab.mit.edu). This project analyzes the impact of the  host ER proteostasis network on the mutational tolerance of human immunodeficiency virus (HIV) envelope (Env). This analysis primarily uses [dms_tools2](https://jbloomlab.github.io/dms_tools2/index.html).

## Abbreviations used

 * Mt1, Mt2, and Mt3 are used to indicate biological replicate 1, 2, and 3, respectively

 * D, T, DT, and V are used to indicate dox-treated (+XBP1s), TMP-treated (+ATF6), dox- and TMP-treated (+XBP1s/+ATF6). and vehicle-treated (Basal) samples, respectively

 * pLAI is used to indicate p0 mutant viral library

 * WT is used to indicate wild-type Env

## Analysis

### 1. Calculating codon counts from FASTQ files

This analysis processes FASTQ files generated by Barcoded-subamplicon sequencing and converts them to codon counts, which are the frequencies of mutations at each site of Env. This analysis is performed by analysis_notebook.ipynb and primarily uses [dms2_batch_bcsubamp](https://jbloomlab.github.io/dms_tools2/dms2_batch_bcsubamp.html). dms2_batch_bcsubamp documentation also contains detailed explanation of the output files.

This analysis requires the following input data.

 * The FASTQ files from deep mutational scanning. The FASTQ files can be downloaded from the Sequence Read Archive under SRA project SRP314168 and BioProject PRJNA720817

 * The wildtype Env sequence for the LAI strain used in the experiment. The seqeucne file (LAI_Env_reference.fa) can be found in the main directory.

This analysis generates the following output data. The output files can be found in ./results/rawcodoncounts and ./results/codoncounts

 * For each sample: log file, read statistics file, reads-per-barcode file, barcode statistics file, counts file

 * As summary statistics: log file, bcstats file, codonmuttypes file, codonntchanges file, cumulmutcounts file, depth file, mutfreq file, readsperbc file, readstats file, singlentchanges file

### 2. Calculating differential selection

This analysis calculates [differential selection (diffsel)](https://jbloomlab.github.io/dms_tools2/diffsel.html#diffsel) from codoncounts.csv files. Briefly, differential selection quantifies the relative enrichment of each amino acid substitution at a given site in the selection condition compared to the mock condition. This analysis is performed by analysis_notebook.ipynb and primarily uses [dms2_batch_diffsel](https://jbloomlab.github.io/dms_tools2/dms2_batch_diffsel.html). dms2_batch_diffsel documentation also contains detailed explanation of the output files.

This analysis requires the following input data.

 * codoncounts.csv files generated from dms2_batch_bcsubamp. The input files can be found in ./results/codoncounts

This analysis generates the following output data.

 * For each sample: log file, mutdiffsel file, sitediffsel file

 * As summary statistics: meanmutdiffsel, meansitediffsel, medianmutdiffsel, mediansitediffsel, absolutesitediffselcorr, maxmutdiffselcorr, mutdiffselcorr, positivesitediffselcorr, meanmaxdiffsel, meanminmaxdiffsel, meanpositivediffsel, meantotaldiffsel, medianmaxdiffsel, medianminmaxdiffsel, medianpositivediffsel, mediantotaldiffsel
