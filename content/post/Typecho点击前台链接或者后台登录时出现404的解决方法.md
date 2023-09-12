---
title: 'Typecho点击前台链接或者后台登录时出现404的解决方法'
description: 'Typecho点击前台链接或者后台登录时出现404的解决方法'
keywords: 'Typecho点击前台链接或者后台登录时出现404的解决方法'

date: 2022-11-24T10:02:47+08:00
lastmod: 2023-09-12T11:59:21+08:00

categories:
  - Typecho
tags:
  - Typecho
abbrlink: '1077'
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
#url: "typecho点击前台链接或者后台登录时出现404的解决方法.html"
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

# Typecho 点击前台链接或者后台登录时出现 404 的解决方法

时间:2022-05-31

本文章向大家介绍 Typecho 点击前台链接或者后台登录时出现 404 的解决方法，主要内容包括其使用实例、应用技巧、基本知识点总结和需要注意事项，具有一定的参考价值，需要的朋友可以参考一下。

{% asset_img typecho_icon.jpg [img1] %}

Typecho 这个开源博客系统的问题我之前就想发出来的，但是因为博客没有 Typecho 的分类，也不太研究 Typecho 就暂时放着了

前段时间我在折腾阿里云赠送的服务器时，安装了下`Typecho`这个程序，使用军哥一键包安装的 LNMP，这里大概说一下我遇到的问题吧

### 1、安装程序时无法连接数据库

在把程序放到目录下，进行安装的时候，将数据库的密码输入正确后，无法进行安装

这个时候处理方式就是手动创建一个`typecho`的数据库即可解决

<!--more-->

### 2、无法登录后台

Nginx 服务器点击前台链接或者后台登录时出现`404, not found`

官方给的解决方式是一般的出现这种情况时，`nginx.conf`里的`location`设置都是类似这样

```
location ~ .*.php$
```

要支持 pathinfo，要改成

```
location ~ .*.php(/.*)*$
```

在某些老版本的 php 里面，可能还要打开 php.ini 里的`cgi.fix_pathinfo`

```
cgi.fix_pathinfo = 1
```

我没有按照这个来，页面 404 一般都是伪静态的问题，在军哥的一键包中有伪静态设置，在添加的时候默认使用了`other.conf`，这里要换成`typecho.conf`

军哥的一键包中默认已经有了一些常用的 Nginx 伪静态配置文件，可以直接输入名称进行使用

我选择使用 wordpress 的配置，修改原来的伪静态配置，配置文件在：`/usr/local/nginx/conf/vhost/域名.conf`

把`include other.conf;`改为`include wordpress.conf;`

执行：**/etc/init.d/nginx restart** 重启生效

然后访问是没有问题了，但是点击登陆又是 404，真是问题一个接一个

把`enable-php.conf`修改为下面这个配置 然后重启 nginx 服务即可

```
location ~ [^/].php(/|$)
{
        #try_files $uri =404;
        fastcgi_pass  unix:/tmp/php-cgi.sock;
        fastcgi_index index.php;
        include fastcgi.conf;
        include pathinfo.conf;
}
```
