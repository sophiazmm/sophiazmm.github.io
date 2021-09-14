---
title: 解决Rstudio报错“Error in plot.new() - figure margins too large”
date: 2021-07-28 23:00:00
categories: DataScience
tags:
  - R
---
![image-20210820160757122](/Users/sophia/Library/Application Support/typora-user-images/image-20210820160757122.png)

解决方法一：

RSTUDIO的四分窗口中plot的窗口过小，把窗口拖大

解决方法二：

图的边距太小，就是边距设置的太大。一个是确实小，`par("mar")`可以查看，可以通过`par(mar=c(1,1,1,1))`修改

