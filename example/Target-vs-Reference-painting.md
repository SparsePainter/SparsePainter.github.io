---
title: Target-vs-Reference painting
layout: single
sidebar:
  nav: "docs"
---

The [example dataset](https://github.com/YaolingYang/SparsePainter/tree/main/example) is available on GitHub. This example includes 8000 reference individuals from 4 populations with 2091 SNPs (Both vcf version ``donor.vcf.gz`` and phase version ``donor.phase.gz`` are available), and the aim is to paint 500 target individuals (Both vcf version ``target.vcf.gz`` and phase version ``target.phase.gz`` are available) using the reference data for **local ancestry estimates**, including **computing LDA, LDAS and AAS**. We can paint with the following command:

*  If your input file is in vcf or vcf.gz format:

``
./SparsePainter -reffile donor.vcf.gz -targetfile target.vcf.gz -popfile popnames.txt -mapfile map.txt -namefile targetname.txt -out target_vs_ref -prob -chunklength -chunkcount -aveSNP -aveind -sample
``

*  If your input file is in phase of phase.gz format:

``
./SparsePainter -reffile donor.phase.gz -targetfile target.phase.gz -popfile popnames.txt -mapfile map.txt -namefile targetname.txt -out target_vs_ref -prob -chunklength -chunkcount -aveSNP -aveind -sample
``

The output file for this example includes ``target_vs_ref_prob.txt.gz``, ``target_vs_ref_chunklength.txt.gz``, ``target_vs_ref_chunkcount.txt.gz``, ``target_vs_ref_aveSNPprob.txt``, ``target_vs_ref_aveindprob.txt``, ``target_vs_ref_samples.txt.gz`` and ``target_vs_ref_fixedlambda.txt``.

If you want to compute LDA, LDAS or AAS, simply add -LDA, -LDAS or -AAS at the end of the above commands.
