---
title: Extract_output
layout: single
sidebar:
  nav: "docs"
---

We have provided the C++ and R codes (C++ is much faster than R) to extract the local ancestry probabilities of certain SNPs from different output formats (constant, linear or raw) in the folder [process_output](https://github.com/YaolingYang/SparsePainter/process_output), which also includes the example data files.

The .cpp files with suffix ``_hap.cpp`` extract probabilities for each haplotype, and those without ``_hap.cpp`` extract probabilities for each diploid individual, i.e. average over two copies.

For example, to extract the local ancestry probabilities of 5000 SNPs (whose indices are contained in ``chr19_GWAS_SNPs.txt``) stored in constant form with C++, we first compile with

``g++ extract_prob_constant.cpp -o extract_constant -lz -std=c++0x -g -O3``

Then we should specify 4 arguments: `npop` (the number of reference populations), `probfile` (local ancestry probabilities file), `SNPfile` (the indices (starting from 1) of the SNPs whose local ancestry probabilities are to be extracted) and `out` (the prefix of the output file).

``./extract_constant -npop 26 -probfile chr19_1000G_constant_10inds_prob.txt.gz -SNPfile chr19_GWAS_SNPs.txt -out chr19_1000G_constant``

Then the probabilities for each reference population (for all the individuals and selected SNPs) are extracted in one gzipped text file.

It works similarly for extracting paintings in the linear form:

``g++ extract_prob_linear.cpp -o extract_linear -lz -std=c++0x -g -O3``

``./extract_linear -npop 26 -probfile chr19_1000G_linear_10inds_prob.txt.gz -SNPfile chr19_GWAS_SNPs.txt -out chr19_1000G_linear``

We do not suggest storing in the raw form, as it's not memory-efficient.
