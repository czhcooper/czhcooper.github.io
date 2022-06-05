---
layout:     post
title:      "Snakemake Tutorial"
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

Here, we created an example workflow of genome analysis, which includes several steps from **reads mapping to a reference genome** to **variants calling**.

### Step 1: Mapping reads

Firstly, we create a new file called `Snakefile` with an editor of your choice (I used `vim` here). In the `Snakefile`, define the following rule:

```python
rule bwa_map:
    input:
        "data/genome.fa",
        "data/samples/A.fastq"
    output:
        "mapped_reads/A.bam"
    shell:
        "bwa mem {input} | samtools view -Sb - > {output}"
```

A `Snakemake` rule has a name (here `bwa_map`) and a number of directives, here `input`, `output` and `shell`. The `input` and `output`  are just explicit Python string.



Notably, it's compulsory to specify the maximum number of CPU cores to use at the same time. If you want to use N cores, say `--cores  N` or `-cN`. For all cores on your system (be sure that this is appropriate) use `--cores all`. For no parallelization use `--cores 1` or `-c1`.











