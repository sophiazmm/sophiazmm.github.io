---
title: BLAST序列比对
date: 2021-08-28 23:00:00
categories: DataScience
tags:
  - BLAST
  - Linux
---

**一、Linux搭建Blast**

1. Blast下载
   下载链接：https://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/LATEST/
   根据服务器系统选择下载版本：
   ![](https://tva1.sinaimg.cn/large/008i3skNly1gughxty7cnj60ze0o6n5g02.jpg)
2. Blast解压安装
   tar -xvf ncbi-blast-2.12.0+-x64-linux.tar
   mv ncbi-blast-2.12.0+-x64-linux.tar blast
3. 配置环境变量
   vim ~/.bashrc
   文件末尾添加：export PATH=/data/software/blast/bin:$PATH
   source ~/.bashrc
4. 检验是否安装成功
   blastn -h 
   ![](https://tva1.sinaimg.cn/large/008i3skNly1gugi45uklpj30y80l6gqd.jpg)

**二、Blastn序列比对**

1. 搭建参考基因组数据库
   文件位置pwd: /data
   下载参考基因组文件：          https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/000/223/135/GCF_000223135.1_CriGri_1.0/GCF_000223135.1_CriGri_1.0_genomic.fna.gz
   mkdir db
   mv GCF_000223135.1_CriGri_1.0_genomic.fna.gz db/
   cd db/
   gunzip GCF_000223135.1_CriGri_1.0_genomic.fna.gz
   makeblastdb -in GCF_000223135.1_CriGri_1.0_genomic.fna -dbtype nucl
   
2. 短序列与参考基因组比对
   文件位置pwd: /data/software/blast
   比对命令：blastn -query seq.fasta -db ../../db/GCF_000223135.1_CriGri_1.0_genomic.fna -out seq.out -outfmt 6 -num_threads 23 -task blastn-short #blastn-short为针对小于30bp序列比对的设定参数
   结果文件：
   ![](https://tva1.sinaimg.cn/large/008i3skNly1gugij45o1vj615o0j243q02.jpg)
   结果文件含12列，信息如下：
   qseqid      query or source (e.g., gene) sequence idsseqid      subject  or target (e.g.,     reference genome) sequence id
   pident      percentage of identical matches
   length      alignment length (sequence overlap)
   mismatch    number of mismatches
   gapopen     number of gap openings
   qstart      start of alignment in query
   qend        end of alignment in query
   sstart      start of alignment in subject
   send        end of alignment in subject
   evalue      expect value
   bitscore    bit score