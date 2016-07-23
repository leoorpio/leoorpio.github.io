 ---
layout: post
date: 2016-07-23 11:19:58 +0800
title: linux 学习篇四-SSH
categories: com-basic
tags:
 - linux
---

SSH为Secure Shell的缩写，由IETF的网络小组（NetWork Working Group）所制定。其是建立在应用层和传输层基础上的安全协议。专门为远程登录会话和其他网络服务提供安全性的协议。  

我们可以在[OpenSSH](http://www.openssh.com/)这关于SSH的相关信息。

[SSH介绍](http://man.openbsd.org/OpenBSD-current/man1/ssh.1)

参考博客：[Ubuntu环境下SSH的安装及使用](http://www.cnblogs.com/rond/p/3688529.html)  

文章提到，SSH分为客户端和服务端。  
服务端是一个守护进程，一般是sshd进程，在后台运行并响应来自客户端的请求。提供了对远程请求的处理，一般包括公共密钥认证、密钥交换、对称密钥加密和非安全连接。  
客户端一般是ssh进程，另外还包含scp、slogin、sftp等其他进程。  


###  安装
   Ubuntu 下安装OpenSSH Server可以通过如下命令：  
```
 sudo apt-get install openssh-server
``` 

###  验证是否启动SSH

```  
ps -e | grep sshd
```  

如果看到有`sshd`项，说明已经启动了。


###  配置
ssh-server配置文件位于 etc/sshd_config。在这里，可以定义SSH的服务端口，默认端口是22。我们可以自己定义其他端口。

配置好后，我们需要重启SSH服务：

```
/etc/init.d/ssh stop
/etc/init.d/ssh start
```  


或者输入命令重启SSH服务器：

```
/etc/init.d/ssh restart
```  


然后我们可以在终端输入如下命令连接登录SSH了:
```
ssh [-p:端口号]@ip:[/directory] 
```  
