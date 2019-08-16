# bismark-file-converter
### This Bismark_to_Permeth_DSS.py script takes a [Bismark](https://github.com/FelixKrueger/Bismark) cytosine report that has been processed to merge symmetric CpG sites and converts it to two legacy formats utilized by the LaSalle lab (Permeth and DSS).

This script was developed to be the last step in the [CpG_Me](https://github.com/ben-laufer/CpG_Me) pipeline, where it utilizes the merged Bismark cytosoine reports generated via `coverage2cytosine --merge_CpG` to provide continuity with existing pipelines. 

## Inputs 

1. Specify a Bismark cytosine report, which contains the following data columns:

| chromosome | start position | end position  | % methylated  | count methylated | count unmethylated |
| ---------- | -------------- | ------------- | ------------- | ---------------- | ------------------ |

2. The following genomes are currently supported: hg38, hg19, mm10, mm9, rheMac8, and rn6.

3. The number of cores to use should be specified by a single integer, where each core requires 25 GB of RAM. 

## Outputs

1. Permeth (percent methylation) format bed files for each chromosome are generated in the 'Permeth' directory in the working directory. 
(Chromosomes of interest vary depending on the type of genome specified but are all subsets of chromosomes 1-22, X, Y, and M.)
Permeth format files contain the following data columns:

| chromosome | start position | end position | % methylated-sumReads | blank00  | strand | blank01 | blank02 | color | 
| ---------- | -------------- | ------------ | --------------------- | ---------| ------ | ------- | ------- | ----- |

Permeth files are intended to be used with [WGBS_Tools](https://github.com/kwdunaway/WGBS_Tools/tree/perl_code), where they may be used to generate 20kb windows of methylation via `Window_permeth_readcentric.pl` and windows for regions of interest, such as CpG islands, via `AvgMeth.2col.pl`.

2. DSS format files for each chromosome of interest are generated in the 'DSS' directory in the working directory.
DSS format files contain the following data columns:

| chr = chromosome | pos = start position | N = count methylated + count unmethylated  | X = count methylated  |
| ---------------- | -------------------- | ------------------------------------------ | --------------------- |

DSS files are intended for use with statistical methods to call DMRs, such as [bsseq](https://bioconductor.org/packages/release/bioc/html/bsseq.html) and [DSS](https://bioconductor.org/packages/release/bioc/html/DSS.html). One example workflow that utilizes these files is [DMRfinder](https://github.com/cemordaunt/DMRfinder). 
