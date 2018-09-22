# bismark-file-converter
This Bismark_to_Permeth_DSS.py script converts a Bismark format file to Permeth (percent methylation) and DSS format files. 

Inputs: 

1. Specify a Bismark format file, which contains the following data columns:
[chromosome] [start position] [end position] [% methylated] [count methylated] [count unmethylated]

2. Genome names must be specified as one of the following: hg38, hg19, rheMac8, rn6, mm9, mm10.

3. The number of cores to use should be specificed by a single integer. 

Outputs:

1. Permeth format bed files for each chromosome of interest in the Bismark format file should be generated in the 'Permeth' directory in the working directory. 
(Chromosomes of interest vary depending on the type of genome specified but are all a subset of chromosomes 1-22, X, Y, and M.)
Permeth format files contain the following data columns:
[chromosome] [start position] [end position] [% methylated-sumReads] [placeholder00] [strand] [placeholder01] [placeholder02] [color] 

2. DSS format files for each chromosome of interest in the Bismark format file should be generated in the 'DSS' directory in the working directory.
DSS format files contain the following data columns:
[chr = chromosome] [pos = start position] [N = count methylated + count unmethylated] [X = count methylated]

