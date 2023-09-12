---
title: 'Hexo博客使用hexo Admin插件管理文章'
description: 'hexo博客使用hexo-admin插件管理文章'
keywords: 'hexo博客使用hexo,admin插件管理文章'

date: 2022-08-25T15:13:00+08:00
lastmod: 2023-09-12T11:58:05+08:00

categories:
  - HEXO个人博客搭建
tags:
  - hexo
  - hexo-admin
  - 文章管理
  - 默认值
  - github
author: 任浪漫
abbrlink: 1345941684
# 原文作者
# Post's origin author name
#author:
# 原文链接
# Post's origin link URL
#link:
# 图片链接，用在open graph和twitter卡片上
# Image source link that will use in open graph and twitter card
#imgs:
# 在首页展开内容
# Expand content on the home page
#expand: true
# 外部链接地址，访问时直接跳转
# It's means that will redirecting to external links
#extlink:
# 在当前页面关闭评论功能
# Disabled comment plugins in this post
#comment:
#  enable: false
# 关闭文章目录功能
# Disable table of content
#toc: false
# 绝对访问路径
# Absolute link for visit
#url: "hexo博客使用hexo-admin插件管理文章.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
# 开启数学公式渲染，可选值： mathjax, katex
# Support Math Formulas render, options: mathjax, katex
#math: mathjax
# 开启各种图渲染，如流程图、时序图、类图等
# Enable chart render, such as: flow, sequence, classes etc
#mermaid: true
---

hexo 博客使用 hexo-admin 插件管理文章

<!--more-->

[hexo 博客使用 hexo-admin 插件管理文章](https://blog.51cto.com/u_15477117/4919720)

[链接 2](https://blog.csdn.net/nineya_com/article/details/103384546)

原创[玖涯博客](https://blog.51cto.com/u_15477117) 2022-01-13 10:35:35

<!-- more -->

## 写在前面

本文主要描述了怎么使用 hexo-admin 插件，hexo-admin 的基本配置问题，各种问题。文章可能还有很多不足，请大家谅解，欢迎大佬提意见。

## 本文使用的东西

1. win10 电脑
2. hexo 3.1.0
3. hexo-admin 2.3.0

## 1.安装

安装 hexo-admin 只需要一条命令

```sh
npm install hexo-admin --save1.
```

当然如果你有配置淘宝的数据源可以使用下面的命令，安装时网络会稍微稳定一些，插件不大，感觉也差不多。

```sh
cnpm install hexo-admin --save1.
```

可能在安装时还会出现一些缺少依赖的问题，我这里没有遇到，直接安装就运行成功了。所以在安装上要是还遇到什么其他问题的就只能你自己度娘了，也可以截图留言给我，看到都会回复的。

![hexo博客使用hexo-admin插件管理文章_hexo-admin](https://s2.51cto.com/images/blog/202201/01000619_61cf2a7bdf07e88376.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=)

## 2.使用

### 2.1 普通使用

输入“`hexo`”运行 hexo，打开浏览器输入“<http://localhost:4000/admin>”，现在就可以正常使用了。

```sh
http://localhost:4000/admin1.
```

![hexo博客使用hexo-admin插件管理文章_hexo-admin_02](https://s2.51cto.com/images/blog/202201/01000620_61cf2a7c065ee85105.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=)

### 2.2 安全设置

在 hexo 的“`_config.yml`”文件中还可以配置一些 hexo-admin 插件的参数，用于保证安全的。如果是部署到 GitHub pages 上的话就没必要设置这个，因为 GitHub 只支持静态，而且 hexo-admin 的管理界面并不会一起被部署上去。

1.在 hexo 的“`_config.yml`”文件中添加以下参数

```sh
admin:
  username: 用户名
  password_hash: md5密码
  secret:  用于加密cookie的密码1.2.3.4.
```

“`_config.yml`”的参数可以使用 hexo-admin 自动生成，打开 hexo-admin 界面，点击导航的“settings”选项，输入内容。

![hexo博客使用hexo-admin插件管理文章_hexo_03](https://s2.51cto.com/images/blog/202201/01000620_61cf2a7c2509512369.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=)

输入内容后下滑，找到生成的代码，复制到“`_config.yml`”中重启 hexo，打来 hexo-admin 的界面。

![hexo博客使用hexo-admin插件管理文章_hexo-admin_04](https://s2.51cto.com/images/blog/202201/01000620_61cf2a7c3f5d450229.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=)

**注意**：

这里要注意的是“`secret`”一定一定不能太过于简单，我设置“123456”报错了，后来我再乱输了一堆字母，，，，，成功。

![hexo博客使用hexo-admin插件管理文章_hexo-admin_05](https://s2.51cto.com/images/blog/202201/01000620_61cf2a7c5de4d58702.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=)

### 2.3 hexo-admin 新建文章设置参数

在 hexo-admin 新建文章可以设置一些文章参数，文章参数配置如下，参数默认值可以为空：

```sh
# hexo-admin默认文章参数
metadata:
  参数名1: 参数默认值2
  参数名2: 参数默认值21.2.3.4.
```

示例：

```sh
# hexo-admin默认参数
metadata:
  author_id: defaultAuthorId
  language:1.2.3.4.
```

![hexo博客使用hexo-admin插件管理文章_hexo-admin_06](https://s2.51cto.com/images/blog/202201/01000620_61cf2a7c71e9928880.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=)

### 2.4linux 自动提交脚本

在“`_config.yml`”的“admin”参数中加入一个子参数“`deployCommand: './admin_script.sh'`”

![hexo博客使用hexo-admin插件管理文章_文章管理_07](https://s2.51cto.com/images/blog/202201/01000620_61cf2a7c810a86651.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=)

在 hexo 博客目录下新建“`admin_script.sh`”文件，输入以下内容：

```sh
#!/usr/bin/env sh
hexo clean
hexo g  -d1.2.3.
```

本人是 windows 系统，该方法未实践过，不知道可不可行。看过官方的 GitHub，都没有提过“`deployCommand`”这个东西。

可能在这个插件的使用中会出现一些问题，比如图片插入失败等问题。在另一篇文章里我讲述这些问题的解决方法，我是通过修改源码解决问题的，同时附带了修改后的补丁。见我另一篇文章：hexo-admin 插件 windows 系统插入图片失败问题解决，hexo-admin 汉化，通过修改源码完美解决，以及插件的一点点优化

## 3.总结

我在使用 hexo-admin 的时候有时候还是会出现一些问题，如果有不清楚的地方欢迎评论留言，看到的我都会回复的。本文到此结束，有什么不足的地方请大家不吝指正。
