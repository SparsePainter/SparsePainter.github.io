---
title: Installation
layout: single
sidebar:
  nav: "docs"
---

# Installation

To install SparsePainter, please follow the below steps.  

``git clone https://github.com/YaolingYang/SparsePainter``  
``cd SparsePainter``  
``wget -O armadillo-12.6.5.tar.xz "https://sourceforge.net/projects/arma/files/armadillo-12.6.5.tar.xz/download"``  
``tar -xf armadillo-12.6.5.tar.xz``  
``mv armadillo-12.6.5 armadillo``  
``cd armadillo``    
``cmake .``  
``cd ..``  
``make``  

Note that SparsePainter depends on [Armadillo](https://arma.sourceforge.net/download.html) to compute AAS and [gzstream](https://www.cs.unc.edu/Research/compgeom/gzstream/) to read the write gzipped files.
