---
title: Extract_output
layout: single
sidebar:
  nav: "docs"
---

To paint large biobanks, it is suggested to split the target samples into multiple (hundreds of) subfiles and paint them separately, which saves memory and computational time. However, people may prefer merge the results of those analyses into a single file for subsequent analysis. Here we explain how to do this for each output.

* ``-prob`` (for any storage mode): 
Retain the first subfile, and then append the rows (excluding the first two rows) of the other subfiles.  

* ``-chunklength`` and ``-chunkcount``:
Retain the first subfile, and then append the rows (excluding the first row) of the other subfiles. To obtain genome-wide chunk length and chunk count, please sum over all chromosomes. 

* ``-aveindpainting``:
Retain the first subfile, and then append the rows (excluding the first row) of the other subfiles.  To obtain genome-wide average painting for individuals, please compute the weighted average of all chromosomes (weighted by the number of SNPs in each chromosome).

* ``-aveSNPpainting``:
Compute the weighted average of all subfiles (weighted by the number of samples in each subfile).

* ``-LDA`` and ``-LDAS``:
Compute the weighted average of all subfiles (weighted by the number of samples in each subfile).

* ``-AAS``:
AAS cannot be directly merged. To obtain the overall AAS, please run SparsePainter without -AAS, but with -aveSNPpainting. Then compute the weighted average of all subfiles (weighted by the number of samples in each subfile). Then compile ``doAAS.cpp`` (contained in the folder [process_output](https://github.com/YaolingYang/SparsePainter/tree/main/process_output))  with below or similar commands (depending on your device, see ``Makefile``):

``g++ -I./armadillo-12.6.5/include doAAS.cpp -o doAAS -lz -fopenmp -lpthread -L./armadillo-12.6.5 -larmadillo -llapack -lblas -std=c++0x -g -O3 -Wl,-rpath=./armadillo-12.6.5``

Finally run the code:

``./doAAS -aveSNPfile [your weighted average aveSNPpainting file] -out [your output file prefix]``
