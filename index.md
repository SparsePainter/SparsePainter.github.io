---
title: SparsePainter -- an efficient software for chromosome painting
layout: single
sidebar:
  nav: "docs"
---

[SparsePainter](https://github.com/YaolingYang/SparsePainter) is an efficient tool for local ancestry inference (LAI) coded in C++. It improves **PBWT** algorithm to find K longest matches at each position, and uses the **Hash Map** strategy to implement the forward and backward algorithm in the Hidden Markov Model (HMM) because of the sparsity of haplotype matches. SparsePainter incorporates the function for efficiently calculating [Linkage Disequilibrium of Ancestry (LDA), LDA score (LDAS)](https://github.com/YaolingYang/LDAandLDAscore) and [Ancestry Anomaly Score (AAS)](https://github.com/danjlawson/ms_paper) for understanding the population structure, evolution, selection, etc..  

-   Authors:  
    Yaoling Yang (<yaoling.yang@bristol.ac.uk>)  
    Daniel Lawson (<dan.lawson@bristol.ac.uk>) 
