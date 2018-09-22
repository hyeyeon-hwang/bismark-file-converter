# bismark-file-converter
This script converts Bismark format files into Permeth (percent methylation) and DSS format files. 

Input 1: Bismark format file
The input to this converter script is a Bismark format file, which contains the following data columns:
[chromosome] [start position] [end position] [% methylated] [count methylated] [count unmethylated]

Input 2: Genome
Genome names must be specified as one of the following: hg38, hg19, rheMac8, rn6, mm9, mm10.

Input 3: Number of cores to use
Specify a single integer. 

Output 1: Permeth format files
The script outputs Permeth format bed files for each chromosome of interest in the Bismark format file. 
(Chromosomes of interest vary depending on the type of genome specified but are all a subset of chromosomes 1-22, X, Y, and M.)
Permeth format files contain the following data columns:
[chromosome] [start position] [end position] [% methylated-sumReads] [placeholder00] [strand] [placeholder01] [placeholder02] [color] 

Output 2: DSS format files
The script also output DSS format files for each chromosome of interest in the Bismark format file. 
DSS format files contain the following data columns:
[chr = chromosome] [pos = start position] [N = count methylated + count unmethylated] [X = count methylated]

