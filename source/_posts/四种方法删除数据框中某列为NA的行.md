---
title: 四种方法删除数据框中某列为NA的行
date: 2021-07-07 23:00:00
categories: DataScience
tags:
  - R
---

**fpkm_host_filter=subset(fpkm_host, !is.na(X))##删除第一列为NA的行base版本**

**fpkm_host_filter3 <- fpkm_host[!is.na(fpkm_host$X),]##删除第一列为NA的行另一个base版本
**

**library(tidyverse)
fpkm_host_filter2=fpkm_host%>% drop_na(X)##删除第一列为NA的行tidyverse极乐版本**

**fpkm_host_filter4=fpkm_host%>%dplyr::filter(!is.na(X))##删除第一列为NA的行tidyverse另一个极乐版本**

