---
title: 解决R语言载入包（library(org.Rn.eg.db)）报错
date: 2021-04-18 23:00:00
categories: DataScience
tags:
  - R
---

解决R语言载入包（library(org.Rn.eg.db)）报错：Loading required package: BiocGenerics
Error in value[[3L\]](https://github.com/Bioconductor/GenomicRanges/issues/cond) :
Package ‘BiocGenerics’ version 0.30.0 cannot be unloaded:
分析原因：安装可能已损坏

解决方法：重新启动R，

并执行如下操作，显示TRUE：

```
library(BiocManager)
BiocManager::valid()
```

再次运行导入，成功