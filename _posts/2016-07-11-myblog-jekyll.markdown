---
layout: post
title:  关于Jekyll blog 一二
date:   2016-07-11 14:52:57 +0800
categories: jekyll
tags:
  - Jekyll
---
   陶小淘：这是我的第一个自己做的博客，虽然简单，我在后期会不断丰富。写下这篇文章，一是勉励自己，二是作为个人能力成长的记载体。                                           

### 1.为什么选择Jekyll+GitHub ？  
 
	Jekyll（发音/'dʒiːk əl/，"杰克尔"）是一个静态站点生成器，它会根据网页源码生成静态文件。
	它提供了模板、变量、插件等功能，所以实际上可以用来编写整个网站。

1. 一位前端网页制作爱好者，个人blog就像自己的心血一样，是自己的一部分。
2. Hexo+GitHub与Jekyll+GitHub，在之前，最先学的是Jekyll入门，于是直接用Jekyll搭建个人博客。
3. 两者GitHub上都能找到很多templates。

### 2. 说在前面（preface）
   第一次接触如何搭建Jekyll静态博客，从这里入手[搭建一个免费的，无限流量的Blog----github Pages和Jekyll入门](http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html) 的，阮一峰前辈的一篇文章。

### 3. 接下来  
  
#### 3.1 前提（precondition）
   1. 拥有个人的GitHub账号，如果没有，赶快去注册一个吧：[传送门](https://www.github.com "github官网")
   2. 慕课网有关于**GitHub**的教程：[传送门](http://www.imooc.com/learn/390)
   3. 这里有关于如何使用**Git**的教程：[传送门](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)，如果想快速上手，可以百度一下Git的常用命令大全。
   4. 如果遇到问题了，可到网站上搜索，可能会在GitHub的**issues**中找到。


#### 3.2 Method 1
   可以像阮前辈（如上链接）的教程简单搭建个人博客，然后根据文档配置一下内容。这个直接上手有些复杂，因为配置文件`_config.yml`有很多东西。需要看一下官方[Jekyll docs](https://jekyllrb.com/docs/home/ "Jekyll使用文档")了解关于配置的内容。重要的是，看的时候有种不知所以然的感觉。
   于是我选择了后面的方法。

#### 3.3 Method 2
  在Jekyll的GitHub项目[Jekyll](https://github.com/jekyll/jekyll)下有一个模板链接[Sides](https://github.com/jekyll/jekyll/wiki/sites)，找一些自己喜欢的。然后fork或者download他们的GitHub上的源码，也可以在知乎上找了一些大家推荐的。
  我喜欢这位[Hux Blog](https://github.com/Huxpro/huxpro.github.io)的博客风格，我也保存下来了。
  有了喜欢的模板，可以直接在拿过来作为自己的博客风格。**注意作者对于版权的要求**。然后适当修改配置和删掉原作者`_posts`和`照片目录`等相关文件，然后加入自己的内容。发布到自己的GitHub上。在直接套用可能会遇到一些语法不了解的。那么你可以从下面这几个网站找到自己的答案：
  
* [Jekyll 英文文档](https://jekyllrb.com/docs/home/ "Jekyll 文档 en-us")
* [Jekyll 中文文档，这里面会有翻译不精确的地方，仅供参考](http://jekyllcn.com/ "Jekyll 文档zh-cn")
* [Jekyll 简单教程](http://www.zhanxin.info/jekyll/2013-08-07-jekyll-doc-installation.html "简单教程")
* Liquid语法：[Liquid for Designers](https://github.com/shopify/liquid/wiki/liquid-for-designers "Liquid grammer" "Liquid grammer")

#### 3.4 Method 3  
   我选择的是第三种方法。自己参考文档、一些好的Blog GitHub源码。在本地生成Jekyll，适当修改自己的样式风格，里面的配置，目录等，然后上传到自己的GitHub上。  
   我用的是Windows 10 x64。根据官方文档的[本地Jekyll使用要求](https://jekyllrb.com/docs/installation/)。我们需要安装如下内容到本地电脑,我以本人的Windows来作介绍。

   * [Ruby](https://www.ruby-lang.org/en/downloads/)
   * [RubyGems](https://rubygems.org/pages/download "对Ruby进行组件打包的Ruby打包系统")
   * OS（Linux，Unix，Mac OSX，Windows）
   * [Node.js](https://nodejs.org/en/),, or another JavaScript runtime (Jekyll 2 and earlier, for CoffeeScript support).
   * [Python 2.7](https://www.python.org/downloads/)。
  
> **提示**：
> 安装的时候注意的软件的配置要求。对于Windows下安装Ruby，可参考这篇百度经验：[传送门](http://jingyan.baidu.com/album/48b558e33558ac7f38c09aee.html?picindex=4)。建议解压DevKit时，不要解压到Ruby的安装目录。



以上安装完成。我们可以在命令窗口中检验一下。  

```bash
C:\Users\xxx>python -V(大写)
Python 2.7.12

C:\Users\xxx>ruby -v
ruby 2.2.4p230 (2015-12-16 revision 53155) [x64-mingw32]

C:\Users\xxx>gem -v
2.6.6

C:\Users\xxx>npm -v
2.14.12
```

然后安装Jekyll，本人现在用的是`jekyll 3.1.6`稳定版本。  

```bash
C:\Users\xxx>gem install Jekyll
```

这里的操作，可以参考官方文档。  
需要注意的是。安装的时候，根据官网文档的提示。如果安装了预览版。在`jekyll serve`命令下时，会遇到这样的错误。详情看这里：[传送门](https://github.com/jekyll/jekyll/issues/4677)。出现的错误提示如下：  

```bash
jekyll 3.2.0.pre.beta1 | Error:  different prefix: "/" 
```

当时自己就蒙了。还好在[Jekyll](https://github.com/jekyll/jekyll "GitHub的Jekyll项目")中找到。这是Windows的下预览版本的一个bug，于是卸载了预览版本。安装了`jekyll 3.1.6`稳定版本。  

可以在命令窗口中通过`gem list`查看已经安装了哪些**ruby**组件：  

```bash
C:\Users\xxx>gem list

*** LOCAL GEMS ***

activesupport (5.0.0)
addressable (2.4.0)
bigdecimal (default: 1.2.6)
coffee-script (2.4.1)
coffee-script-source (1.10.0)
colorator (0.1)
concurrent-ruby (1.0.2)
ethon (0.9.0)
execjs (2.7.0)
faraday (0.9.2)
ffi (1.9.13 x64-mingw32)
gemoji (2.1.0)
github-pages (87)
github-pages-health-check (1.1.0)
html-pipeline (2.4.2)
i18n (0.7.0)
io-console (default: 0.4.3)
jekyll (3.1.6)
```

我只列出了部分。想要卸载哪一个，可以通过`gem uninstall <gems's name>`来卸载指定的`<gems's name>`文件。我就是通过`gem uninstall jekyll`来卸载了Jekyll的预览版。重新安装了Jekyll。  

通过命令窗口运行`jekyll serve`或`jekyll serve --watch`时，如果出现错误提示，可能是关于缺少包的，这是需要通过`gem <gems's name>`来安装指定的`<gems's name>`文件。  

	在搭建的过程中。我用了三天时间。一天看Jekyll的文档，了解其内容，还有Liquid tags的语法。 
 
	第二天自己找模板，自己简单设计自己想要什么风格的。然后开始修改Jekyll目录结构下的相关内容。
	
	第三天调整一下自己的blog。

#### 3.5 需要掌握的内容

1.  Jekyll的目录结构
2.  Jekyll的`_config.yml`哪些配置选项
3.  YMAL Front Matter 的作用和参数
4.  ...

#### 3.6 难点  

1. 关于配置文件 `_config.yml`里面的内容还真不少。文档简单的介绍。但是用的时候会一头雾水。查看其它人多模板时，发现用的格式也不一。看了几遍之后，目前大体有了认识。

2. 在本地运行jekyll时候，会遇到包找不到的问题，第一次接触rubygems,运行出错的提示看不懂，尝试在stackoverflow找答案。没有找到。后来明白是缺少包的缘故。于是运行的时候，缺少什么，我就到[传送门](https://rubygems.org/)到这里搜。如当时自己遇到的是bundle包的问题。然后自己找到安装链接。然后在命令窗口中：

```bash
gem install bundle
``` 

#### 3.7 需要注意的地方
1. 理解Jekyll的目录结构
2. Jekyll渲染后文件目录的所在位置
3. _post目录下文件的命名格式
4. YAML Front matter，_config.yml不要用Tag，用空格进行缩减  


----------------------------
以上是一些大体的介绍，具体的操作需要各自去摸索。
