---
title: Usages
layout: single
sidebar:
  nav: "docs"
---

Either variant call format (VCF) or phase format is supported by **SparsePainter**. Inputting phase format is slightly faster than inputting the VCF format. To prepare the phase format for **SparsePainter**, you should get [PBWT](https://github.com/richarddurbin/pbwt) installed, which converts Variant Call Format (VCF) to phase format by the following command:

``
pbwt -readVcfGT XXX.vcf -writePhase XXX.phase
``

To run **SparsePainter**, enter the following command:

``
./SparsePainter [-command1 -command2 ...... -command3 parameter3 -command4 parameter4 ......]
``

# Commands

## Required Commands

**SparsePainter** has below 6 required commands together with additional commands that specify the desired output.

* **-reffile [file]** Reference vcf (including gzipped vcf), or phase (including gzipped phase) file that contains the genotype data for all the reference samples.

* **-targetfile [file]** Reference vcf (including gzipped vcf), or phase (including gzipped phase) file that contains the genotype data for each target sample. To paint reference samples against themselves, please set ``targetfile`` to be the same as ``reffile``. The file type of ``targetfile`` and ``reffile`` should be the same.

* **-mapfile [file]** Genetic map file that contains two columns with the first line specifying the column names. The first column is the SNP position (in base) and the second column is the genetic distance of each SNP (in Morgan). The number of SNPs must be the same as that in ``reffile`` and ``targetfile``.

* **-popfile [file]** Population file of reference individuals that contains two columns. The first column is the names of reference samples (must be in the same order as ``reffile``). The second column is the population indices of the reference samples. The population indices must be non-positive integers ranging from 0 to k-1, assuming there are k different populations in the reference panel.

* **-namefile [file]** Name file that contains the names of samples to be painted.

* **-out [string]** Prefix of the output file names (**default=SparsePainter**).

**At least one of the below commands should also be given in order to run SparsePainter**

* **-prob** Output the local ancestry probabilities for each target sample at each SNP. The output file format is a gzipped text file (.txt.gz). The output probabilities need to be standardized by user because of the rounding errors by argument ``dp``.

* **-chunklength** Output the chunk length of each local ancestry for each target sample. The output file format is a gzipped text file (.txt.gz).

* **-aveSNP** Output the average local ancestry probabilities for each SNP. The output file format is a text file (.txt).

* **-aveind** Output the average local ancestry probabilities for each target individual. The output file format is a text file (.txt).

* **-LDA** Output the LDA of each pair of SNPs. The output file format is a gzipped text file (.txt.gz). It might be slow: the computational time is proportional to the number of local ancestries and the density of SNPs in the chromosome.

* **-LDAS** Output the LDAS of each SNP. The output file format is a text file (.txt). It might be slow: the computational time is proportional to the number of local ancestries and the density of SNPs in the genome.

* **-AAS** Output the AAS of each SNP. The output file format is a text file (.txt).

## Optional Commands

### Commands without values

* **-haploid** The individuals are haploid.

* **-diff_lambda** Use different recombination scaling constants for each target sample. If this command is not given, the fixed lambda will be output in a text file (.txt) for future reference.

* **-loo** Paint with leave-one-out strategy: one individual is left out of each population (self from own population). If `-loo` is not specified under reference-vs-reference painting (`reffile=targetfile`), each individual will be automatically left out of painting.

* **-rmrelative** Leave out the reference sample that is the most related to the target sample under leave-one-out mode (`-loo`), if they share at least ``relafrac`` proportion of SNPs.

### Commands with values

* **-ncores [integer&ge;0]** The number of CPU cores used for the analysis (**default=0**). The default **ncores** uses all the available CPU cores of your device.

* **-fixlambda [number&ge;0]** The value of the fixed recombination scaling constant (**default=0**). **SparsePainter** will estimate lambda as the average recombination scaling constant of ``indfrac`` target samples under the default ``fixlambda`` and ``diff_lambda``.

* **-nmatch [integer>=1]** The number of haplotype matches of at least ``L_minmatch`` SNPs that **SparsePainter** searches for (**default=10**). Positions with more than ``nmatch`` matches of at least ``L_minmatch`` SNPs will retain at least the longest ``nmatch`` matches. A larger ``nmatch`` slightly improves accuracy but significantly increases the computational time.

* **-L0 [integer>0]** The initial length of matches (the number of SNPs) that **SparsePainter** searches for (**default=320**). ``L_initial`` must be bigger than ``L_minmatch`` and preferrably be a power of 2 of ``L_minmatch`` for computational efficiency.

* **-Lmin [integer>0]** The minimal length of matches that **SparsePainter** searches for (**default=20**). Positions with fewer than ``nmatch`` matches of at least ``L_minmatch`` SNPs will retain all the matches of at least ``L_minmatch``. A larger ``L_minmatch`` increases both the accuracy and the computational time.

* **-method [Viterbi/EM]** The algorithm used for estimating the recombination scaling constant (**default=Viterbi**).

* **-probstore [raw/constant/linear/cluster]** Output the local ancestry probabilities in raw, constant, linear or cluster form (**default=constant**). For each haplotype, in ``raw`` form, we output the probabilities of each SNP with the SNP name being their physical positions in base; in ``constant`` form, we output the range of SNP index, and the painting probabilities that those SNPs share; in ``linear`` form, we output the range of SNP index, and the painting probabilities of the start SNP and the end SNP, while the intermediate SNPs are estimated by the simple linear regression with root mean squared error smaller than ``rmsethre``; in ``cluster`` form, we perform K-means clustering on the painting of each haplotype with ``ncluster`` clusters and maximum ``max_ite`` iterations, and output the average probabilities of each cluster and the cluster of each SNP. Storing in ``constant`` considerably reduces the file size while has the same accuracy compared with storing in ``raw``; storing in ``linear`` has an even smaller file size but becomes slightly slower and loses some accuracy; storing in ``cluster`` has the smallest file size but with slowest speed.

* **-dp [integer>0]** The decimal places of the output of local ancestry probabilities (**default=2**). This also controls the size of the output file for local ancestry probabilities.

* **-rmsethre [number&isin(0,1)]** The upper bound that the root mean squared error of the estimated local ancestry probabilities (**default=0.01**) when storing them in linear form by argument, i.e. ``-probstore linear``.

* **-relafrac [number&isin;(0,1)]** The proportion of the total number of SNPs shared between a reference and target haplotype sample (**default=0.2**). The reference sample will be removed under the leave-one-out (``-loo``) and remove relative (``-rmrelative``) modes.

* **-ncluster [integer>0]** The number of clusters (**default=100**) for K-means clustering under ``-probstore cluster`` mode.

* **-kmeans_ite [integer>0]** The number of maximum iterations (**default=30**) for K-means clustering under ``-probstore cluster`` mode.

* **-SNPfile [file]** File contains the specific physical position (in base) of the SNPs whose local ancestry probabilities are output in the raw form. If this file is not specified (default), then all the SNPs' local ancestry probabilities will be output in the form specified by ``probstore``. 

* **-indfrac [number&isin;(0,1)]** The proportion of individuals used to estimate the recombination scaling constant (**default=0.1**).

* **-minsnpEM [integer>0]** The minimum number of SNPs used for EM algorithm if ``-method EM`` is specified (**default=2000**).

* **-EMsnpfrac [number&isin;(0,1)]** The proportion of SNPs used for EM algorithm if ``-method EM`` is specified (**default=0.1**). Note that if ``nsnp*EMsnpfrac < minsnpEM``, ``minsnpEM`` SNPs will be used for EM algorithm.

* **-EM_ite [integer>0]** The iteration times for EM algorithm if ``-method EM`` is specified (**default=10**).

* **-window [number>0]** The window for calculating LDA score (LDAS) in Morgan (**default=0.04**).

* **-matchfile [file]** The file name of the set-maximal match file which is the output of [pbwt -maxWithin](https://github.com/danjlawson/pbwt/blob/master/pbwtMain.c). This can only be used for painting reference samples against themselves. When ``matchfile`` is given, there is no need to provide ``reffile`` and ``targetfile``, because all the match information required for painting is contained in ``matchfile``. Using set-maximal matches is not recommended because set-maximal matches are extremely sparse and will significantly reduce the accuracy, despite saving compute time.
