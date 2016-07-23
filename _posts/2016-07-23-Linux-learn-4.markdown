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

工作机制：   

1. 客户端发送一个连接请求到远程服务端  
2. 服务端检查申请的包和IP地址，再发送密钥给SSH客户端  
3. 客户端再将密钥发回服务端，自此建立链接。  

（客户端的安装不是必须的）  

###  1 服务端的安装
   Ubuntu 下安装OpenSSH Server可以通过如下命令：  
```
 sudo apt-get install openssh-server
``` 

###  2 验证是否启动SSH

```  
ps -e | grep sshd
```  

如果看到有`sshd`项，说明已经启动了。


### 3 配置
ssh-server配置文件位于 etc/sshd_config。在这里，可以定义SSH的服务端口，默认端口是22。我们可以自己定义其他端口

```
vim /etc/ssh/sshd_config
```


配置好后，我们需要重启SSH服务：

```
/etc/init.d/ssh stop  #停止
/etc/init.d/ssh start  #重启
```  


或者输入命令重启SSH服务器：

```
/etc/init.d/ssh restart
```  


然后我们可以在终端输入如下命令连接登录SSH了:
```
ssh [-p:端口号]@ip:[/directory] 
```  

### 4 Tips
相对于传统的网络服务程序，如：ftp、pop和Telnet在本质上都是不安全的，因为他们在网络上用明文传送口令和数据，有心人很容易截取这些口令和数据。使用SSH，可以把所有传输的数据进行加密。  
SSH有很多功能，它既可以代替Telnet，又可以为FTP、PoP、甚至PPP提供一个安全的”通道”。 