---
title: SparsePainter -- fast, accurate and fine-scale chromosome painting software
sidebar:
  nav: "docs"
---

[**SparsePainter**](https://github.com/YaolingYang/SparsePainter) is an efficient tool for local ancestry inference (LAI) coded in C++. It extends **PBWT** algorithm to find K longest matches at each position, and uses the **Hash Map** structure to implement the forward and backward algorithm in the Hidden Markov Model (HMM) leveraging the sparsity of haplotype matches. SparsePainter can infer **fine-scale local ancestry** (per individual per SNP) and **genome-wide total ancestry**, it also enables efficiently calculating [**Linkage Disequilibrium of Ancestry (LDA), LDA score (LDAS)**](https://github.com/YaolingYang/LDAandLDAscore) and [**Ancestry Anomaly Score (AAS)**](https://github.com/danjlawson/ms_paper) for understanding the population structure, evolution, selection, etc.

SparsePainter also produces output required to run [**GLOBETROTTER**](https://github.com/hellenthal-group-UCL/GLOBETROTTER), [**fastGLOBETROTTER**](https://github.com/hellenthal-group-UCL/fastGLOBETROTTER) and [**SOURCEFIND**](https://github.com/hellenthal-group-UCL/sourcefindV2) ([example codes](https://github.com/will-camb/misc/blob/main/sparsepainter2sourcefind.py) to run SOURCEFIND based on SparsePainter output are available).   

**SparsePainter GitHub repository:** [https://github.com/YaolingYang/SparsePainter](https://github.com/YaolingYang/SparsePainter)

**PBWTpaint GitHub repository:** [https://github.com/richarddurbin/pbwt](https://github.com/richarddurbin/pbwt)

**SparsePainter and PBWTpaint Reference: [Yang, Y., Durbin, R., Iversen, A.K.N & Lawson, D.J. Sparse haplotype-based fine-scale local ancestry inference at scale reveals recent selection on immune responses. Nature Communications 16, 2742 (2025).](https://www.nature.com/articles/s41467-025-57601-3)**

**LDA, LDA score and AAS reference and use cases:** [Barrie, W., Yang, Y., Irving-Pease, E.K. et al. Elevated genetic risk for multiple sclerosis emerged in steppe pastoralist populations. Nature 625, 321–328 (2024).](https://www.nature.com/articles/s41586-023-06618-z)

**Pipeline for** [biobank-scale painting](https://github.com/YaolingYang/SparsePainter/tree/main/painting-pipeline/standard%20painting) and [computing haplotype components (HCs)](https://github.com/YaolingYang/SparsePainter/tree/main/painting-pipeline/Compute%20haplotype%20components%20(HCs)) **are available.**

**PBWTpaint GitHub Repository:** [https://github.com/richarddurbin/pbwt](https://github.com/richarddurbin/pbwt)

**A use case of HCs:** [Yang, Y., Lawson, D.J. From individuals to ancestries: towards attributing trait variation to haplotypes. medRxiv (2025), doi: https://doi.org/10.1101/2025.03.13.25323895.](https://www.medrxiv.org/content/10.1101/2025.03.13.25323895v1)

-   Authors:  
    Yaoling Yang (<yaolingyang1998@gmail.com>)  
    Daniel Lawson (<dan.lawson@bristol.ac.uk>)

-   Maintainer:  
    Yaoling Yang (<yaolingyang1998@gmail.com>)

-   Version: 1.3.2

**SparsePainter** is a direct improvement of [ChromoPainter](https://people.maths.bris.ac.uk/~madjl/finestructure-old/chromopainter_info.html) and is orders of magnitudes faster.

The detailed [installation instructions](https://sparsepainter.github.io/Installation.html), 
[usages and commands](https://sparsepainter.github.io/Usages.html), and examples are available.  

The main usage of **SparsePainter** is to perform [Target-vs-Reference painting](https://sparsepainter.github.io/example/Target-vs-Reference-painting.html) for local ancestry estimates, and
[Reference-vs-Reference painting](https://sparsepainter.github.io/example/Reference-vs-Reference-painting.html) for admixture estimation. [PBWTpaint](https://github.com/richarddurbin/pbwt) has extraordinary performance in doing 
[All-vs-All painting](https://sparsepainter.github.io/example/All-vs-All-painting.html) for clustering and learning haplotype principal components. 

Here is an overview of the functionalities of SparsePainter and PBWTpaint.

![overview](/images/overview.png)

