---
title: Installation
layout: single
sidebar:
  nav: "docs"
---

To install SparsePainter, please follow the below steps.  

``git clone git@github.com:YaolingYang/SparsePainter.git``  
``cd SparsePainter``  
``make``  

Note that SparsePainter requires g++ >=6 and depends on   
[Armadillo-v12.6.5](https://arma.sourceforge.net/download.html) to compute AAS;   
[gzstream-v1.5](https://www.cs.unc.edu/Research/compgeom/gzstream/) to read and write gzipped files.

To update the newer version of SparsePainter, you can remove lines 10-12 of Makefile, since armadillo has already been installed during your initial installation.
