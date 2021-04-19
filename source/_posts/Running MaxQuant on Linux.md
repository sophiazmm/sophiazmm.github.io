---
title: Linux安装应用MaxQuant
date: 2021-04-18 23:00:00
categories: DataScience
tags:
  - Linux
  - MaxQuant
---
MaxQuant官方文档：http://www.coxdocs.org/doku.php?id=maxquant:start

## 一、MaxQuant下载
https://maxquant.org/download_asset/maxquant/latest
![](https://tva1.sinaimg.cn/large/008eGmZEly1gpgsq4dwt6j30ws0u00uz.jpg)
填写的邮箱里获取下载链接，七日有效

## 二、Install .NET Core 2.1
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb 
sudo dpkg -i packages-microsoft-prod.deb

sudo apt-get update; \ 
sudo apt-get install -y apt-transport-https && \
sudo apt-get update && \ 
sudo apt-get install -y dotnet-sdk-2.1
![](https://tva1.sinaimg.cn/large/008eGmZEly1gpgsuet0brj317w03s3ze.jpg)
这里显示版本号，可以直接运行；
否则，自行安装https://dotnet.microsoft.com/download/dotnet/2.1

## 三、生成/编辑XML文档
1. 自动生成，生成命令行：
python3 Maxquant.py  maxquant_linux_guide-master/templates/SILAC.xml rawdata_file/  -o /mnt/data/output_mqpar.xml  -t 6
Maxquant.py模版链接：https://github.com/atc3/maxquant_linux_guide/blob/master/gen_mqpar.py
2. 编辑xml文件
主要涉及以下几个参数：
![](https://tva1.sinaimg.cn/large/008eGmZEly1gpgvnvldbzj31ye0ag0wm.jpg)
![](https://tva1.sinaimg.cn/large/008eGmZEly1gpgvouhdmij31pu0r8gu7.jpg)

## 四、运行MaxQuant
dotnet MaxQuant/bin/MaxQuantCmd.exe mqpar.xml
mono  MaxQuant/bin/MaxQuantCmd.exe mqpar.xml

## 五、MaxQuant其他参考文档
http://www.coxdocs.org/doku.php?id=:maxquant:start
https://atchen.me/research/2019/03/21/mq-linux.html
https://github.com/atc3/maxquant_linux_guide
https://pharmazie.unigreifswald.de/storages/unigreifswald/fakultaet/mnf/pharma/biotechno/dokumente/MaxQuant_Infos_and_Tutorial_07.pdf
https://www.researchgate.net/post/Why-MaxQuant-on-Linux-crashes-when-Mono-is-installed-from-the-source-but-not-when-it-is-installed-form-the-repository
