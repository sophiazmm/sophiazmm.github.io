---
title: Linux安装mono
date: 2021-04-17 23:00:00
categories: DataScience
tags:
  - Linux
  - mono
---
mono官方文档：https://www.mono-project.com/

The latest Stable Mono release is: **6.12.0 Stable (6.12.0.122)**

## 1. 添加mono存储库##
sudo apt install gnupg ca-certificates

sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF  echo "deb https://download.mono-project.com/repo/ubuntu stable-focal main" | sudo tee /etc/apt/sources.list.d/mono-official-stable.list
sudo apt update
## 2. 安装mono##
sudo apt install mono-devel
sudo apt install  mono-complete
sudo apt install  mono-dbg
sudo apt install  referenceassemblies-pcl 
sudo apt install  ca-certificates-mono 
sudo apt install  mono-xsp4
## 3.确定安装 ##

> 要测试可用的最基本功能，请将以下代码复制到名为hello.cs的文件中:using System;public class HelloWorld {public static void Main(string[] args) { Console.WriteLine ("Hello Mono World"); } }
> 要编译，使用csc：csc hello.cs
> 编译器将创建“ hello.exe”，可以使用以下命令运行它：mono hello.exe
> ![](https://tva1.sinaimg.cn/large/008eGmZEly1gpgrttzso6j317c070n0d.jpg)
> HTTPS连接：为了确保HTTPS连接正常运行，请运行以下命令(csharp -e 'new System.Net.WebClient ().DownloadString ("https://www.nuget.org")')以检查是否可以连接到nuget.org：如果一切正常，该程序将打印网站内容，否则将引发异常。如下图所示，http连接正常
> ![](https://tva1.sinaimg.cn/large/008eGmZEly1gpgs7rq9kgj31ma0jods2.jpg)
> 确认mono版本: mono -- version
> ![](https://tva1.sinaimg.cn/large/008eGmZEly1gpgsed10hyj310c0c6te0.jpg)

