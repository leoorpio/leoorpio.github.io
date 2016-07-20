---
layout: post
date: 2016-07-19 14:10:08 +0800
title: linux 学习篇二
categories: com-basic
tags:
 - linux
---
   继续ing，参考自《鸟哥的Linux私房菜》。

### 1 Linux 用户与用户组  
假设这个系统上有两片资源，分别是A区和B区。其中A区有三个人A1，A2，A3组成，B由B1，B2组成。A中的A1，A2，A3都有私有的不能见光的，他们可以享有Ａ区的资源，Ａ区和Ｂ区都是在Ｒ的地盘上。那么  
用户（User）概念：用户之间不能相互访问对方私有资源，如A1，A2之间。  
用户组（Group）概念：可以享有共同访问某一资料的用户集，A1，A2，A3组成用户组。  
其他人（Other）概念：A区的几位和B区之间的几位的关系，如果不是自家区域的人，都算是其他人。  
root：万能的用户。

* Linux用户身份和用户组记录的文件  

```
`/etc/passwd`：在Linux的系统中，默认的情况下所有的系统的账号与一般身份用户，还有root的相关信息，都记录在这个文件内。  
`etc/shadow`：记录个人的密码。  
`etc/group`：记录Linux所有的组名。
```  

平时切换到root，可以在终端工具输入命令：sudo su，然后输入密码。退出可以按`Ctrl+d`。


### 2 Linux文件属性

```bash
zoro@ubuntu:~$ ls -al
总用量 136
drwxr-xr-x 20 zoro zoro 4096 7月  19 17:08 .
drwxr-xr-x  3 root root 4096 7月  18 16:23 ..
-rw-------  1 zoro zoro  303 7月  19 17:14 .bash_history
-rw-r--r--  1 zoro zoro  220 7月  18 16:23 .bash_logout
-rw-r--r--  1 zoro zoro 3771 7月  18 16:23 .bashrc
drwx------ 16 zoro zoro 4096 7月  18 18:52 .cache
drwx------ 23 zoro zoro 4096 7月  18 20:53 .config
drwx------  3 zoro zoro 4096 7月  18 18:23 .dbus
-rw-r--r--  1 zoro zoro   25 7月  18 16:41 .dmrc
drwxr-xr-x  3 zoro zoro 4096 7月  18 17:04 Documents
drwxr-xr-x  2 zoro zoro 4096 7月  18 17:21 Downloads
-rw-r--r--  1 zoro zoro 8980 7月  18 16:23 examples.desktop
drwx------  2 zoro zoro 4096 7月  19 17:08 .gconf
drwx------  3 zoro zoro 4096 7月  19 17:08 .gnupg
......
```

- 其中我们会看到上面的有七列。

```  
	第一列代表这个文件的类型与权限
	第二列表示有多少个文件名连接到此节点
	第三列表示这个文件（或目录）的“所有者账号”
	第四列表示这个文件的所属用户组
	第五列为这个文件的容量大小，默认单位为B
	第六列表示这个文件的创建日期或最近的修改日期
	第七列为该文件名
```

- 第一列

```
    10位字符组成:[-]<sup>1</sup> [---]<sup>2</sup> [---]<sup>3</sup> [---]<sup>4</sup>。  
    第一个字符代表这个文件是“目录、文件、或链接文件等”。
    [d]则是目录，例如上面的`.gconf`
    [-]则是文件，例如上面的`.examples.desktop`
    [l]则表示为链接文件
    [b]则表示设备文件里面的可供存储的接口设备
    [c]则表示设备文件里面的串行端口设备，例如键盘、鼠标等（一次性读取设备）
```

接下来的字符中，以三个为一组，均为`rwx`,[r]代表可读read，[w]代表为可写write，[x]代表可执行execute。  

```  
    第一组：文件所有者的权限
    第二组：同组用户的权限
    第三组：其他非本用户组的权限
```

### 3 改变文件属性和权限
- chgrp（change group）：改变文件所属用户组  

```
    格式：
    chgrp [-R] groupname dirname/filename
```

- chown（change owner）：改变文件所有者

```
  格式：
  chown [-R] 账号名称 文件或目录
  chown [-R] 账号名称：组名 文件或目录
```

- chmod（）：改变文件的权限  
  两种方法：  
  ** 一是通过数字类型改变文件权限；**

```
    各权限的分数对照表如下：
	r:4
	w:2
	x:1
    各种身份（owner、group、others）各自的三个权限是需要累加的，例如，当权限为【-rwxrwx---】，分数则是：
    owner = 4 + 2 + 1 = 7
    group = 4 + 2 + 1 = 7
    others = 0 + 0 + 0 = 0
    所以等一下我们设置权限的更改是，该文件的权限数字是770，更改权限的命令chmod的语法是这样的：
    [root@www~ ]# chmod [-R] xyz 文件或目录
```
  
  **二是通过符号来进行权限的更改。**  

```
    User（u）：具有可读、可写、可执行的权限
    group与others（g/o）：具有可读与执行的权限。
```
举个例子：

```
[root@www~ ]# chmod u=rwx,go=rx 文件或目录

```  
