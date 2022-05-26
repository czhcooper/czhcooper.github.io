---
layout:     post
title:      "Snakelike Tutorial"
author:     "Cooper"
header-img: "img/post-bg-2015.jpg"
catalog: true
typora-root-url: ../
tags:
    - Bioinformatic tools
    - Python
---

# Introduction





`Snakemake` integrates with the package manager `conda` and the container engine `Signlarity`

Snakemake is a general purpose workflow management system not only for *Bioinformatics* but also for any *discipline*.

`mamba` is a package manager, which is similar to `conda` but faster than `miniconda`. It's recommended to use `mamba` to install `snakemake` ,but it's not necessary. Alternatively, you can install `snakemake` just using `conda`.



A `Snakemake` workflow is defined by specifying rules in a `Snakefile` , in which rules decompose the workflow into small steps.

Here, we created an example workflow of genome analysis, which includes several steps such as **reads mapping to a reference genome** and **variants calling**.



