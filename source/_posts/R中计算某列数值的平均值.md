---
title: 两种R中计算某列数值的平均值方法
date: 2021-06-18 23:00:00
categories: DataScience
tags:
  - R
---
**apply**

apply(fpkm_host_filter,2,mean)###apply(cluster1,2,mean) 将函数“mean”应用于第二维（列）

**colMeans**

colMeans(fpkm_host_filter, na.rm=TRUE)###使用colMeans计算列的平均值