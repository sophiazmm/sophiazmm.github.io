---
title: qqman&ggplot两种方法制作曼哈顿图
date: 2021-05-18 23:00:00
categories: DataScience
tags:
  - R
  - qqman
  - ggplot
---

data <-read.table("ratio.xls", header = T)
head(data)

![image-20210607114640672](/Users/sophia/Library/Application Support/typora-user-images/image-20210607114640672.png)


#(一)qqman

install.packages("qqman")
library(qqman)
head(gwasResults)
data <- read.table("ratio.xls", header = T)
nrow(data)
data$SNP <- seq(1,525369)
head(data)

![image-20210607114259114](/Users/sophia/Library/Application Support/typora-user-images/image-20210607114259114.png)manhattan(data, chr="Chr", bp="Start", snp="SNP", p="Ratio",col = c("blue", "orange"), cex.axis=1.0, cex=0.6)



#(二)ggplot

install.packages("dplyr") 
install.packages("ggplot2")

library(dplyr)
data$BP <- data$Start/1000000
don <- data %>%

group_by(Chr) %>%
summarise(chr_len = max(BP)) %>%

mutate (tot = cumsum(chr_len)-chr_len) %>%
select(-chr_len) %>%

left_join(data, ., by=c("Chr" = "Chr")) %>%

arrange(Chr, BP) %>%
mutate(BPcum = BP+tot)

axisdf = don %>% group_by(Chr) %>% summarise(center= (max(BPcum)+min(BPcum))/2)

library(ggplot2)
ggplot(don, aes(x=BPcum, y=-log10(Ratio))) +
geom_point(aes(color=as.factor(Chr)), alpha=0.8, size=1.3) +
  scale_color_manual(values = rep(c("blue", "orange"),22)) +
  scale_x_continuous(labels = axisdf$Chr, breaks = axisdf$center) +
  scale_y_continuous(expand = c(0,0)) +
  theme_bw() +
  theme( 
      legend.position="none",
      panel.border = element_blank(),
      panel.grid.major.x = element_blank(),
      panel.grid.minor.x = element_blank()
  )