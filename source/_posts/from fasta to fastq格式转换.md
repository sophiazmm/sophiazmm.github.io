---
title: from fasta to fastq
date: 2021-08-08 23:00:00
categories: DataScience
tags:
  - python
  - perl
---

1. 基于perl

*cat 1tar_seq.fasta | paste - - | perl -ne 'chomp; s/^>/@/; @v = split /\t/; printf("%s\n%s\n+\n%s\n", $v[0], $v[1], "B"x length($v[1]))' > 1tar_seq.fq*

2. 基于python包bioconvert

*bioconvert fasta2fastq 1tar_seq.fasta 1tar_seq.bioconvert.fq*

3. 基于python包pyfastaq

*pip3 install pyfastaq*
*fastaq to_fake_qual 1tar_seq.fasta - | fastaq fasta_to_fastq 1tar_seq.fasta - 1tar_seq.pyfastaq.out.fastq*