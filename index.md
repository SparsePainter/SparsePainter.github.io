---
title: SparsePainter -- an efficient software for chromosome painting
sidebar:
  nav: "docs"
---

[SparsePainter](https://github.com/YaolingYang/SparsePainter) is an efficient tool for local ancestry inference (LAI) coded in C++. It improves **PBWT** algorithm to find K longest matches at each position, and uses the **Hash Map** strategy to implement the forward and backward algorithm in the Hidden Markov Model (HMM) because of the sparsity of haplotype matches. SparsePainter incorporates the function for efficiently calculating [Linkage Disequilibrium of Ancestry (LDA), LDA score (LDAS)](https://github.com/YaolingYang/LDAandLDAscore) and [Ancestry Anomaly Score (AAS)](https://github.com/danjlawson/ms_paper) for understanding the population structure, evolution, selection, etc..  

You can find the [introduction](https://sparsepainter.github.io/), 
[installation instructions](https://sparsepainter.github.io/Installation.html), 
[usages and parameters](https://sparsepainter.github.io/Usages.html) and Examples.  

The main usage of **SparsePainter** is to perform [Target-vs-Reference painting](https://sparsepainter.github.io/example/Target-vs-Reference-painting.html) for local ancestry estimates, 
[Reference-vs-Reference painting](https://sparsepainter.github.io/example/Reference-vs-Reference-painting.html) for admixture estimation, and 
[All-vs-All painting](https://sparsepainter.github.io/example/All-vs-All-painting.html) for clustering.

-   Authors:  
    Yaoling Yang (<yaoling.yang@bristol.ac.uk>)  
    Daniel Lawson (<dan.lawson@bristol.ac.uk>) 
