To decipher reliable signal from experimental noise, we filtered the DMS data using the following two-step strategy. This analysis
(1) removes mutdiffsel values for variants not present in the starting library of the corresponding replicate. Values that are removed are replaced with -100 in an array which is then plotted on a heatmap (where -100 is colored in black).
(2) (a) removes mutdiffsel values that are not present in the starting library of all replicates and (b) removes mutdiffsel values that are not of the same sign (positive or negative) across all replicates. values that are removed are replaced with -100 in the final filtered heatmap files.

########################################

#CodonsToAAs.py

This script converts codon counts file with NNN codons to amino acids, which is needed for downstream analysis.

The order of amino acids is: {0:'G',1:'A',2:'V',3:'I',4:'L',5:'M',6:'F',7:'Y',8:'W',9:'S',10:'T',11:'N',12:'Q',13:'C',14:'P',15:'H',16:'R',17:'K',18:'D',19:'E'}

Input:
    
    codoncounts ### The pLAI codoncounts file from dms2_batch_bcsubamp

Output
    
    AAcounts ### The pLAI codoncounts file converted to amino acid counts


To run:
	
    python CodonsToAAs.py codoncounts.csv AAcounts.txt

########################################

#FilteringStep1.py

This script removes mutdiffsel values for variants not present in the starting library of the corresponding replicate. Values that are removed are replaced with -100 in an array which is then plotted on a heatmap. This script creates heatmaps of (1) unfiltered mutdiffsel values and (2) mutdiffsel values where variants not present in the starting library of the corresponding replicate has been removed.


Inputs:
    
    dmsdiffsel ### The diffsel file from dms2_batch_diffsel
    
    AAcounts ### The amino acid counts file from the output of CodonsToAAs.py

Outputs:
	
    heatmap ### A heatmap file after the first-step filtering

    unfiltered_heatmap ### An unfiltered heatmap file; this file name is automatically generated based on the heatmapfilename specified with "unfiltered" added at the beginning of the file name
    

To run:

    python FilteringStep1.py dmsdiffsel.csv AAcounts.txt heatmap.txt

########################################

#FilteringStep2.py

This script (a) removes mutdiffsel values that are not present in the starting library of all replicates and (b) removes mutdiffsel values that are not of the same sign (positive or negative) across all replicates. values that are removed are replaced with -100 in the final filtered heatmap files.

Inputs:
    
    heatmap1 ### Heatmap after the first-step filtering for replicate 1
    
    heatmap2 ### Heatmap after the first-step filtering for replicate 2

    heatmap3 ### Heatmap after the first-step filtering for replicate 3

Outputs:

    pickoutname ### Mutdiffsel values of the variants that passed both filter 1 and 2, listed in the order of (1) site, (2) amino-acid substitution, (3) average mutdiffsel, (4) mutdiffsel of replicate 1, (5) mutdiffsel of replicate 2, (6) and mutdiffsel of replicate 3). Sites in this file are labelled as "site in LAI numbering" - 35.

    filtered_heatmap1 ### Final heatmap after the second-step filtering for replicate 1; this file name is automatically generated based on the name of heatmap1 specified with "filtered_" added at the beginning of the file name

    filtered_heatmap2 ### Final heatmap after the second-step filtering for replicate 2; this file name is automatically generated based on the name of heatmap2 specified with "filtered_" added at the beginning of the file name

    filtered_heatmap3 ### Final heatmap after the second-step filtering for replicate 3; this file name is automatically generated based on the name of heatmap3 specified with "filtered_" added at the beginning of the file name

To run:

    python FilteringStep2.py heatmap1.txt heatmap2.txt heatmap3.txt pickoutname.txt

#FilteredDiffsel

    This folder contains the final pickout.txt files converted to csv files with column titles. In addition, sites were renumbered according to the HXB2 numbering system. For those sites where no variants survived the filtering, we added the wild-type mutdiffsel back for downstream data analysis. This step was performed manually.