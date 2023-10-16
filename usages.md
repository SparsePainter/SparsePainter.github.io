---
layout: default
title: Usages
---

# Usage

Either variant call format (VCF) or phase format is supported by **SparsePainter**. Inputting phase format is slightly faster than inputting the VCF format. To prepare the phase format for **SparsePainter**, you should get [PBWT](https://github.com/richarddurbin/pbwt) installed, which converts Variant Call Format (VCF) to phase format by the following command:

``
pbwt -readVcfGT XXX.vcf -writePhase XXX.phase
``

To run **SparsePainter**, enter the following command:

``
./SparsePainter [-parameter1 -parameter2 ...... -parameter3 value3 -parameter4 value4 ......]
``
