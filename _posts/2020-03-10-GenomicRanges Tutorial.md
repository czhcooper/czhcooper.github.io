---
layout:     post
title:      "GenomicRanges Tutorial"
subtitle:   
date:       2021-03-10 06:35:00
author:     "Cooper"
header-img: "img/post-bg-2015.jpg"
catalog: true
typora-root-url: ../
tags:
    - Typora
    
---



#Introduction



```
if (!require("BiocManager"))
    install.packages("BiocManager")
BiocManager::install("GenomicRanges")
library(GenomicRanges)
```

Reference: [An Introduction to the GenomicRanges Package](https://bioconductor.org/packages/devel/bioc/vignettes/GenomicRanges/inst/doc/GenomicRangesIntroduction.html)