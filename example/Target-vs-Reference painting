---
layout: default
title: Target-vs-Reference painting
---

# Target-vs-Reference painting
The example dataset is available on [Github](https://github.com/YaolingYang/SparsePainter/example). This example includes 8000 reference individuals from 4 populations with 2091 SNPs (Both vcf version ``donor.vcf.gz`` and phase version ``donor.phase.gz`` are available), and the aim is to paint 500 target individuals (Both vcf version ``target.vcf.gz`` and phase version ``target.phase.gz`` are available) using the reference data for local ancestry estimates. We can paint with the following command:

(a) If your input file is in vcf or vcf.gz format:

``
./SparsePainter -reffile donor.vcf.gz -targetfile target.vcf.gz -popfile popnames.txt -mapfile map.txt -namefile targetname.txt -out target_vs_ref -prob -chunklength
``

(b) If your input file is in phase of phase.gz format:

``
./SparsePainter -reffile donor.phase.gz -targetfile target.phase.gz -popfile popnames.txt -mapfile map.txt -namefile targetname.txt -out target_vs_ref -prob -chunklength
``

The output file for this example includes ``target_vs_ref_prob.txt.gz``, ``target_vs_ref_chunklength.txt.gz``, and ``target_vs_ref_fixedlambda.txt``.
