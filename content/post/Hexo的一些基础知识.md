---
title: 'Hexo的一些基础知识'
description: 'Hexo的一些基础知识'
keywords: 'Hexo的一些基础知识'

date: 2022-08-23T15:18:05+08:00
lastmod: 2023-09-12T11:58:07+08:00

categories:
  - HEXO个人博客搭建
tags:
  - hexo博客搭建
  -
abbrlink: 2929538386

# 原文作者
# Post's origin author name
#author:
# 原文链接
# Post's origin link URL
link: https://blog.csdn.net/jiunian_2761/article/details/122908619
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
#url: "hexo的一些基础知识.html"
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

Hexo 的一些基础知识

原文链接：<https://blog.csdn.net/jiunian_2761/article/details/122908619>

<!-- more -->

## 1 如何新建文章（博客）？

假设我要新建标题为 小白的逆袭之路 文章，我们进入**Hexo**博客主目录，在命令行操作下执行：

```shell
hexo new post "小白的逆袭之路"
```

文章即会被创建在**博客主目录/source/\_posts**目录中

## 2 如何删除博客

进入**博客主目录/source/\_posts**目录，找到你想删除的文章，鼠标右键删除即可。

## 3 如何编辑博客

Hexo 渲染文章使用 Github 的 GFM 语法 的 Markdown 格式，在编辑文章之前，我强烈建议大家先去了解 Hexo 下 Markdown 的基本语法，上手非常简单。

### 3.1 使用专门的 Markdown 编辑器

目前市面上有许多 Markdown 编辑器，这里我墙裂推荐大家使用 Typora 使用方式以及介绍可以参考 少数派：Typora 完全使用详解

配置好 Typora 后我们编辑文章时只要点击我们要编辑的以 md 结尾的博客文件，鼠标右键 > 打开方式 > 用 Typora 打开

即可用 Typora 编辑器进行编辑。

在足够熟悉 Markdown 语法后，可以使用任意一种文本编辑器编写 Markdown 文件。

### 3.2 使用 Git Bash 的 vim 编辑器

```shell
vim 小白的逆袭之路.md
```

其他的一些文本编辑器类。
VSCode
Sublime
…

## 4 如何为文章添加标签（tags）以及分类（categories）

在我们编辑文章时，文章头部都会有这样的格式：

Hexo 称其为 Front-matter 用于指定个别文件的变量，Hexo 设定了多种参数：
| 参数 | 描述 | 默认值 |
| ------------------------------------------------------------ | -------------------- | ------------------------------------------------------------ |
| layout | 布局 | [`config.default_layout`](https://hexo.io/zh-cn/docs/configuration#文章) |
| `title` | 标题 | 文章的文件名 |
| `date` | 建立日期 | 文件建立日期 |
| `updated` | 更新日期 | 文件更新日期 |
| `comments` | 开启文章的评论功能 | true |
| `tags` | 标签（不适用于分页） | |
| `categories` | 分类（不适用于分页） | |
| `permalink` | 覆盖文章网址 | |
| `excerpt` | Page excerpt in plain text. Use [this plugin](https://hexo.io/docs/tag-plugins#Post-Excerpt) to format the text | |
| `disableNunjucks` | Disable rendering of Nunjucks tag `{{ }}`/`{% %}` and [tag plugins](https://hexo.io/docs/tag-plugins) when enabled | |
| `lang` | Set the language to override [auto-detection](https://hexo.io/docs/internationalization#Path) | Inherited from `_config.yml` |

tag 对应你想对该文章设置的标签 ，书写格式为：- 标签名

categories 指定分类，书写格式为：- 分类名

```shell
    title: 小白的逆袭之路
    tags:
     - 小白    #标签1
     - 励志    #标签2
    categories:
     - Dream #父分类
     - Light Dream #子分类
```

仔细观察的朋友估计已经看出来了，我在分类名后面分别注释了 父分类以及子分类，为什么是这样子呢，根据官方的说明：

```txt
    在Hexo 中，分类和标签有着明显的差别：分类具有顺序性和层次性，而标签没有顺序和层次行。

    区别于WordPress ，WordPress支持对一篇文章设置多个分类，这些分类可以是同级的，也可以是父子分类。但是Hexo不支持指定多个同级分类。例如上面的指定方法，会将分类Light Dream 变为 Dream 的子类，而不是并列分类。因此，在进行您的文章分类时，请尽可能准确的分类。
```

## 5 修改主题配置正确但刷新未显示修改的内容

在每次我们进行主题或者是对站点配置修改后，执行：

```shell
    hexo clean && hexo g && hexo s
```

## 6 TypeError: Cannot read property ‘length’ of null

开始遇到这个问题的时候一脸懵逼，再加上对 Javascript 不熟，所以困扰许久。

首先我们查看异常内容，里面有这一段：

```shell
    node_modules\highlight.js\lib\highlight.js:388:42
```

然后我寻找源码看到这段注释：

```shell
    /*
    Syntax highlighting with language autodetection.
    https://highlightjs.org/
    */
```

语法高亮自动侦测语言？然后我想起来配置文件好像有个侦测语言的，查看了一下站点配置文件找到 highlight：

```shell
    highlight:
      enable: true
      line_number: true
      auto_detect: true #自动判断代码语言
      tab_replace:
```

看到了 auto_detect ，自动判断代码语言，所以应该就是这里。

那么是哪里出了问题呢，我的文章中代码比较复杂但是都指定了语言，这里的自动侦测语言可能遇到比较复杂的代码会检测出问题。

于是我将 auto_detect 改为 false，重新运行 hexo g，成功。

---

```shell
# 查找占用的端口
netstat -aon|findstr 4000

# 查找指定的PID对应的应用程序
tasklist|findstr 8012
node.exe                      8012 Console

tasklist|findstr 4252
FoxitProtect.exe              4252 Services

C:\Windows\system32>http://localhost:4000/hexo/admin/#/pages
```
