---
title: All-vs-All painting
layout: single
sidebar:
  nav: "docs"
---

The example dataset is available on [GitHub](https://github.com/YaolingYang/SparsePainter/tree/main/example).
This example includes 8000 reference individuals with 2091 SNPs (Both vcf version ``donor.vcf.gz`` and phase version ``donor.phase.gz`` are available).   
We want to paint all the individuals against all the individuals for **clustering**. PBWT paint is extremely fast at doing this. 
Please ensure you got [PBWT](https://github.com/richarddurbin/pbwt) installed, and then run with the below commands:

(a) If your input file is in vcf or vcf.gz format:  

``
./pbwt --readVcfGT donor.vcf.gz -paintSparse all_vs_all
``

(b) If your input file is in phase of phase.gz format:

``
./pbwt --readPhase donor.phase.gz -paintSparse all_vs_all
``

The output file for this example includes ``all_vs_all.chunkcounts.s.out.gz``, ``all_vs_all.chunklengths.s.out.gz``,``all_vs_all.regionchunkcounts.s.out.gz``, ``all_vs_all.regionchunklengths.s.out.gz`` and ``all_vs_all.nregions.s.out.gz``.

It is also possible to do All-vs-All painting with SparsePainter, which is slightly more accurate than SPBWTpaint, but is much slower. Note that the popfile ``allvsall_popnames`` assigns each individual a different population, which is the requirement for doing all-vs-all painting.

(a) If your input file is in vcf or vcf.gz format:  

``
./SparsePainter -reffile donor.vcf.gz -targetfile donor.vcf.gz -popfile allvsall_popnames.txt -mapfile map.txt -namefile refname.txt -out all_vs_all -chunklength
``

(b) If your input file is in phase of phase.gz format:

``
./SparsePainter -reffile donor.phase.gz -targetfile donor.phase.gz -popfile allvsall_popnames.txt -mapfile map.txt -namefile refname.txt -out all_vs_all -chunklength
``

The output file for this example includes ``all_vs_all.chunklength.txt.gz``, and ``all_vs_all.fixedlambda.txt``.
