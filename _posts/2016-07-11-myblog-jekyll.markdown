---
layout: post
title:  "关于Jekyll blog 的一二"
date:   2016-07-11 14:52:57 +0800
categories: jekyll
tags:
  - Jekyll
---
   这是我的第一个自己做的博客，虽然简单，在后期会不断丰富。写下这篇文章，一是勉励自己，二是作为个人能力成长的记载体。                       --陶小陶 2016年7月13日13:24:46
## 1. 为什么选择Jekyll+GitHub？
	Jekyll（发音/'dʒiːk əl/，"杰克尔"）是一个静态站点生成器，它会根据网页源码生成静态文件。
	它提供了模板、变量、插件等功能，所以实际上可以用来编写整个网站。

1. 作为一位前端网页制作爱好者，个人blog是必要。
2. Hexo+GitHub与Jekyll+GitHub，之前学了点Jekyll入门，于是直接用Jekyll搭建个人博客看。
3. 两者GitHub上都能找到很多template。

## 2. 说在前面（preface）
   第一次接触如何搭建Jekyll静态博客，从这里入手[搭建一个免费的，无限流量的Blog----github Pages和Jekyll入门](http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html) 的，阮一峰前辈的一篇文章。

## 3. 接下来
### 3.1 前提（precondition）
   1. 拥有个人的GitHub账号，如果没有，赶快去注册一个吧：[传送门](https://www.github.com "github官网")
   2. 慕课网有关于**GitHub**的教程：[传送门](http://www.imooc.com/learn/390)
   3. 这里有关于如何使用**Git**的教程：[传送门](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)，如果想快速上手，可以百度一下Git的常用命令大全。
   4. 如果遇到问题了，到网站上搜索，可能会在GitHub的**issues**中找到。


### 3.2 Method 1
   可以像阮前辈（如上链接）的教程简单搭建个人博客，然后根据文档配置一下内容。这个直接上手有些复杂，因为配置文件`_config.yml`有很多东西。需要看一下官方[Jekyll docs](https://jekyllrb.com/docs/home/ "Jekyll使用文档")关于配置的内容。重要的是，看了也不一定能上手。
   于是我选择了后面的方法。

### 3.3 Method 2
  在Jekyll的GitHub项目[Jekyll](https://github.com/jekyll/jekyll)下有一个链接[Sides](https://github.com/jekyll/jekyll/wiki/sites)，这里有很多模板。我找了一些好看的。然后看他们的GitHub上的源码，download到本地。
  我也在知乎上找了一些大家推荐的。最喜欢这位[Hux Blog](https://github.com/Huxpro/huxpro.github.io)的博客风格，我也保存下来了。
  有了模板，如果你喜欢这套模板，那么你就可以直接在套用。**注意作者对于版权的要求**。在直接套用可能会遇到一些语法不了解的。那么你可以从下面这几个网站找到自己的答案：
* [Jekyll 英文文档](https://jekyllrb.com/docs/home/ "Jekyll 文档 en-us")
* [Jekyll 中文文档，这里面会有翻译不精确，仅供参考]（http://jekyllcn.com/ "Jekyll 文档zh-cn"）
* [Jekyll 简单教程](http://www.zhanxin.info/jekyll/2013-08-07-jekyll-doc-installation.html "简单教程")
* Liquid语法：[Liquid for Designers](https://github.com/shopify/liquid/wiki/liquid-for-designers "Liquid grammer" "Liquid grammer")

### 3.4 Method 3
   我选择的是第三种方法。自己参考文档、一些好的Blog GitHub源码。在本地生成Jekyll然后上传到自己的GitHub上。
   我用的是Windows 10 x64。根据官方文档的[前提要求](https://jekyllrb.com/docs/installation/)。我们需要安装如下内容到本地电脑,我以本人的Windows来写。
   * [Ruby](https://www.ruby-lang.org/en/downloads/)
   * [RubyGems](https://rubygems.org/pages/download "对Ruby进行组件打包的Ruby打包系统")
   * OS（Linux，Unix，Mac OSX，Windows）
   * [Node.js](https://nodejs.org/en/),, or another JavaScript runtime (Jekyll 2 and earlier, for CoffeeScript support).
   * [Python 2.7](https://www.python.org/downloads/)。
> **提示**：
> 安装的时候注意的软件的配置要求。对于Windows下安装Ruby，可参考这篇百度经验：[传送门](http://jingyan.baidu.com/album/48b558e33558ac7f38c09aee.html?picindex=4)。建议解压DevKit时，不要解压到Ruby的安装目录。


以上安装完成。我们可以在命令窗口中检验一下。
```bash
C:\Users\***>python -V(大写)
Python 2.7.12

C:\Users\***>ruby -v
ruby 2.2.4p230 (2015-12-16 revision 53155) [x64-mingw32]

C:\Users\***>gem -v
2.6.6

C:\Users\***>npm -v
2.14.12
```

然后安装Jekyll，本人现在用的是`jekyll 3.1.6`稳定版本。
```bash
C:\Users\***>gem install Jekyll
```
这里的操作，可以参考官方文档。
需要注意的是。当时我安装的时候，根据官网文档的提示。安装了预览版。详情看这里：[传送门](https://github.com/jekyll/jekyll/issues/4677)。出现了提示：
```bash
jekyll 3.2.0.pre.beta1 | Error:  different prefix: "/" 
```
当时自己就蒙了。还好在[Jekyll](https://github.com/jekyll/jekyll "GitHub的Jekyll项目")中找到。然后自己卸载了预览版本。安装了`jekyll 3.1.6`版本。
可以在命令窗口中通过`gem list`查看已经安装了哪些**ruby**组件：
```bash
C:\Users\***>gem list

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

