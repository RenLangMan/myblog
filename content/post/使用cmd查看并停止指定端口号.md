---
title: '使用cmd查看并停止指定端口号'
description: '使用cmd查看并停止指定端口号'
keywords: '使用cmd查看并停止指定端口号'

date: 2023-09-12T11:58:03+08:00
lastmod: 2023-09-12T11:58:03+08:00

categories:
  -
tags:
  -
  -
abbrlink: a861
# 原文作者
# Post's origin author name
#author:
# 原文链接
# Post's origin link URL
link: https://blog.csdn.net/weixin_45652692/article/details/113341562
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
#url: "使用cmd查看并停止指定端口号.html"
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

# 使用 cmd 命令查看并停止指定端口号

1.win+r：打开 cmd 窗口，或者在“开始”中打开运行输入 cmd

<!--more-->

2.进入 cmd 窗口后，输入 `netstat -aon|findstr “8123”` 命令。查看下是哪一个程序占用了`8123`这个端口号；记下程序的 PID 值(比如 1264)。

3.然后输入 `taskkill /pid 1264 -t -f` 就可以将这个占用的 PID 直接关闭。

然后被占用的端口号就释放了。

[csdn 博客原文链接](https://blog.csdn.net/weixin_45652692/article/details/113341562)
