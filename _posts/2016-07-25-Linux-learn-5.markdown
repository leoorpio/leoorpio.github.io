---
layout: post
title: Linux安装配置Java
date: 2016-07-25 13:51:52 +0800
categories: com-basic
tags:
 - linux
 - java

published: false
---  

在此之前，我们先了解一下Ubuntu的目录结构：[传送门](http://www.cnblogs.com/zf2011/archive/2012/05/17/2505847.html)。  

其中`/opt`目录是存放自己安装的应用软件的。我这次把java安装到此处。（个人偏好）  


在[http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)这下载Linux版本的JDK压缩包。
我用的是Ubuntu(Linux) X64的，所以下载了`jdk-8u101-linux-x64.tar.gz`这个压缩包。  
![java下载页选项](../images/01.png)  

下载成功后，我们的文件`jdk-8u101-linux-x64.tar.gz`是下载到：