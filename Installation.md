---
title: Installation
layout: single
sidebar:
  nav: "docs"
---

To install SparsePainter, please follow the below steps.  

``git clone git@github.com:YaolingYang/SparsePainter.git``  
``cd SparsePainter``  
``tar -xf armadillo-12.6.5.tar.xz``  
``mv armadillo-12.6.5 armadillo``  
``cd armadillo``    
``cmake .``  
``cd ..``  
``make``  

Note that SparsePainter depends on [Armadillo](https://arma.sourceforge.net/download.html) to compute AAS and [gzstream](https://www.cs.unc.edu/Research/compgeom/gzstream/) to read the write gzipped files.
