---
layout: post  
date: 2016-7-26 10:48:46 +0800  
title: linux 应用篇一 ：环境变量 
categories: com-basic  
tag:
  - linux
---   

在应用Windows安装一些编程软件（如Java、Ruby、Python等）的时候，我们需要为其配置环境变量。有些应用程序在安装的过程中会提示我们是否添加环境变量，这省去我们手动配置的过程。  
对于Java，在Windows中，我们需要到  

```
我的电脑 | 属性 | 高级系统设置 | 环境变量
```  
### 1 环境变量

对PATH和相关变量进行配置。  

在[维基百科：Environment variable](https://en.wikipedia.org/wiki/Environment_variable)这篇文章里面，我们可以大体了解到在Unix、Linux、OS X和Windows等系统下，我们都会应用到环境变量。  
环境变量是一组动态命名的值（系统运行环境的一些参数）的集合。他们会影响运行中的进程。运行中的进程会根据环境变量所配置的路径去获取路径下的信息。  

我们用Ubuntu的终端命令举个例子来认识一下,在终端命令查看这个用户的环境变量的值：

```bash
zoro@ubuntu:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
zoro@ubuntu:~$ 
```

如果我们把环境变量换一下，如下：
  
```bash
zoro@ubuntu:~$ PATH=/usr/local/sbin
zoro@ubuntu:~$ echo $PATH
/usr/local/sbin

```  

我们把原来的变量后部分去掉了，然后我们用Ubuntu常用命令`ls -a`查看这个目录下有哪些文件夹，看看这个命令能否有效:  

```bash  
zoro@ubuntu:~$ ls -a
命令 'ls' 可在 '/bin/ls' 处找到
由于/bin 不在PATH 环境变量中，故无法找到该命令。
ls：未找到命令

```

我们会发现命令出错，提示为找不到这个命令，正常情况下这个命令是可行的，为什么会这样？接下来我们把再环境变量`$PATH`的值恢复为原来的值，再试一次：

```bash
zoro@ubuntu:~$ PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
zoro@ubuntu:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
zoro@ubuntu:~$ ls -a
.              Documents         .presage                   模板
..             Downloads         .profile                   视频
.bash_history  examples.desktop  .sudo_as_admin_successful  图片
.bash_logout   .gconf            .viminfo                   文档
.bashrc        .gnupg            .Xauthority                下载
.cache         .ICEauthority     .xinputrc                  音乐
.config        .local            .xsession-errors           桌面
.dbus          .mozilla          .xsession-errors.old
.dmrc          .pam_environment  公共的

```  

命令又正常了。通过上面这个简单的例子能对环境变量有一个简单直观的认识。

平时我们允许某个shell命令或开启一个进程，他们需要到系统的环境变量去获取或存储相关信息。  


问题来了，为什么要配置环境变量？  

```  
环境变量包含了一个或者多个应用程序所将使用到的信息，它可以告诉系统，当要求系统运行一个程序而没有告诉它程序所在的完整路径时，系统除了在当前目录下面寻找此程序外，还应到那些目录下去找。
``` 

### 2 Ubuntu下面的环境变量  

 Ubuntu系统下包含两类环境变量：系统环境变量和用户环境变量。  

* 系统环境变量：对所有系统用户都有效；
* 用户环境变量：仅仅对当前的用户有效。
  

用户环境变量通常在以下文件中：

```  
~/.bashrc
~/.profile
``` 

系统环境变量一般保持在下面文件中：

```
/etc/environment
/etc/profile
/etc/bash.bashrc 
```  

### 3 Java的安装及环境配置

在终端命令中查看是否已有java安装：

```bash    
zoro@ubuntu:/etc$ java -version
程序 'java' 已包含在下列软件包中：
 * default-jre
 * gcj-5-jre-headless
 * openjdk-8-jre-headless
 * gcj-4.8-jre-headless
 * gcj-4.9-jre-headless
 * openjdk-9-jre-headless
请尝试：sudo apt install <选定的软件包>
```

如果误装了openjdk，可以在这里找到相关命令移除:[传送门](http://blog.csdn.net/swuteresa/article/details/13335481)  

在Oracle官网下载Linux版本的Java。然后解压到`/opt/java`目录下。首先我们要在这里建一个目录。对于这个目录，一般网友会解压到`/usr/lib/`目录下自己建的文件夹。我这个属于个人偏好。  

```  
cd /opt
mkdir java
sudo tar -zxv -f /下载/java安装包名.tar.gz -C /opt/java
```

在Ubuntu配置Java环境变量时候，我在自己的用户环境变量`~/.bashrc`下配置，在文件最后加入：  

```bash
export JAVA_HOME=/opt/java/dir # 这个dir是解压后java目录下的目录名
export JRE_HOME=${JAVA_HOME}/jre
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
export PATH=${JAVA_HOME}/bin:$PATH 
```

配置好后，通过命令`source ~/.bashrc`立即生效。
然后可以通过`java -version`查看安装结构。