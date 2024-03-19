---
title: Reference-vs-Reference painting
layout: single
sidebar:
  nav: "docs"
---

The [example dataset](https://github.com/YaolingYang/SparsePainter/tree/main/example) is available on GitHub. This example includes 8000 reference individuals from 4 populations with 2091 SNPs (Both vcf version ``donor.vcf.gz`` and phase version ``donor.phase.gz`` are available), and the aim is to paint them against themselves for **admixture estimation**. We can paint with the following command:

(a) If your input file is in vcf or vcf.gz format:

``
./SparsePainter -reffile donor.vcf.gz -targetfile donor.vcf.gz -popfile popnames.txt -mapfile map.txt -namefile refname.txt -out ref_vs_ref -prob -chunklength -loo
``

(b) If your input file is in phase or phase.gz format:

``
./SparsePainter -reffile donor.phase.gz -targetfile donor.phase.gz -popfile popnames.txt -mapfile map.txt -namefile refname.txt -out ref_vs_ref -prob -chunklength -loo
``

The output file for this example includes ``ref_vs_ref_prob.txt.gz``, ``ref_vs_ref_chunklength.txt.gz`` and ``ref_vs_ref_fixedlambda.txt``.
