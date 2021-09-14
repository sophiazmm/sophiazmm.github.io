---
title: 序列比对Bowtie2
date: 2021-09-14 23:00:00
categories: DataScience
tags:
  - Bowtie2
  - Linux
---

**一、Bowtie2下载安装**

1. Bowtie2软件下载
   
   下载链接：下载最新版本
   https://sourceforge.net/projects/bowtie-bio/files/bowtie2/2.4.4/
   根据服务器系统选择软件版本：
   
   ![](https://tva1.sinaimg.cn/large/008i3skNly1gugj54wyv2j61m00icn0g02.jpg)
   
2. Bowtie2软件解压

   文件位置pwd: /data/software

   unzip bowtie2-2.4.4-linux-x86_64.zip

3. 配置环境变量

   vim ~/.bashrc

   文件末尾添加：export PATH=/data/software/bowtie2-2.4.4-linux-x86_64:$PATH

   source ~/.bashrc

4. 检查是否安装成功

   bowtie2 -h

   ![image-20210914223711148](/Users/sophia/Library/Application Support/typora-user-images/image-20210914223711148.png)

**二、Bowtie2短序列比对**

1. 创建Bowtie2的index数据库

   bowtie2-build GCF_000223135.1_CriGri_1.0_genomic.fna GCF

2. 使用Bowtie2进行序列比对

   比对命令及参数：/data/software/bowtie2-2.4.4-linux-x86_64/bowtie2 -x /data/bio-db/GCF -U tar_seq.fq -S tar_bowtie.sam --end-to-end - N 1

   注：--end-to-end: 整个reads与参考基因组进行比对
           -N <int> 进行种子比对时允许的mismatch数. 可以设为0或者1. Default: 0

​    ![image-20210914224737272](/Users/sophia/Library/Application Support/typora-user-images/image-20210914224737272.png)

