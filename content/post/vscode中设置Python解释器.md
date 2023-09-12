---
title: 'Vscode中设置Python解释器'
description: 'vscode中设置Python解释器'
keywords: 'vscode中设置Python解释器'

date: 2022-11-03T12:58:00+08:00
lastmod: 2023-09-12T11:59:24+08:00

categories:
  -
tags:
  -
  -
abbrlink: 80fe
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
#url: "vscode中设置python解释器.html"
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

# [vscode 中设置 Python 解释器 ](https://www.cnblogs.com/devilmaycry812839668/p/16412457.html)

以前在设置 vscode 中的 Python 解释器时都是采用图形化选择的方式来进行的，但是不知怎么的最近这个 vscode 在手动选择解释器时会出现时而好用时而不好用的情况，因此这里又给出了一种通过设置 workspace 下 launch.json 的方式。

说明一下本文假设 vscode 已经成功安装，系统中已经有了多个 Python 解释器，并且 vscode 中已经安装好 Python 的插件。

<!--more-->

**第一种，图形化设置 Python 解释器的方法**：

{% asset_img 001.png [image01] %}

{% asset_img 002.png [image02] %}

{% asset_img 003.png [image03] %}

{% asset_img 004.png [image04] %}

===========================================

**第二种，通过编写 launch.json 文件来设置 Python 解释器的方法**：

以上是通过图形化界面来选择具体的 Python 解释器，但是发现有时候这个自动识别环境的解释器和具体设置的时候会出现问题，有的时候会出现设置不上的情况，于是不得已研究了一下配置项目 launch.json 文件来设置 Python 的解释器。

在主菜单上开始进行选择：

运行》添加配置

出现配置模式选择框，由于在 vscode 中会自动判定你项目的语言，由于项目中已经创建了.py 文件，因此这个工作空间已经被判定为 Python 语言项目，因此这里我们可以看到出现的可供选择的配置模式中的 Python File 就是为 Python 语言项目提供的配置模板。

{% asset_img 005.png [image05] %}

选择 Python File 配置：

{% asset_img 006.png [image06] %}

可以看到在 workspace 空间下自动创建了.vscode 文件夹，并且在 .vscode 文件夹下面自动创建了本项目的配置文件： launch.json 文件。

{% asset_img 007.png [image07] %}

给出为 Python 项目生成的默认配置文件 launch.json 的具体内容：

```json
{
  // 使用 IntelliSense 了解相关属性。
  // 悬停以查看现有属性的描述。
  // 欲了解更多信息，请访问: https://go.microsoft.com/fwlink/?linkid=830387
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Python: Current File",
      "type": "python",
      "request": "launch",
      "program": "${file}",
      "console": "integratedTerminal",
      "justMyCode": true
    }
  ]
}
```

\-----------------------------------------------------------------------------

需要注意的是这个项目空间下的`launch.json`文件既可以是按照上面的操作生成也可以手动在`.vscode`文件夹下面创建。

在上面创建的`launch.json`文件中我们添加`Python`字段并设置解释器路径即可以实现 Python 解释器的指定，这里我个人的设置为：

```json
    "python": "/home/devil/PycharmProjects/py/bin/python",
```

\--------------------------------

{% asset_img 008.png [image08] %}

配置好后执行代码看下效果：

{% asset_img 009.png [image09] %}

可以看到我们手动通过图形化界面指定的 Python 解释器为系统原生的，即`/usr/bin/python3`，但是这个 Python 环境下面并没有安装`pytorch`，同时我们在`launch.json`中指定了其他路径的带有`pytorch`的 Python 解释器，可以看到运行代码的时候现实`pytorch`是可见的。由此可知如果你同时在图形化界面中指定了 Python 解释器并且你还在 launch.json 中指定了 Python 解释器，那么最终 vscode 在执行代码时会优先使用 launch.json 中的 Python 解释器，这也是为什么如果在图形化指定 Python 解释器失效后我们可以通过手动编写 launch.json 文件来进行 Python 解释器的指定。

在 launch.json 中指定 Python 解释器的完整文件：

launch.json

```json
{
  // 使用 IntelliSense 了解相关属性。
  // 悬停以查看现有属性的描述。
  // 欲了解更多信息，请访问: https://go.microsoft.com/fwlink/?linkid=830387
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Python: Current File",
      "type": "python",
      "python": "/home/devil/PycharmProjects/py/bin/python",
      "request": "launch",
      "program": "${file}",
      "console": "integratedTerminal",
      "justMyCode": true
    }
  ]
}
```

=====================================

其他的事情：

虽然在上面的操作中我们通过在`launch.json`文件中指定`Python解释器`实现了在代码调试时优先与图形化界面中指定的 Python 解释器而被选择执行，但是我们如果细致的观察一下 Python 代码就会发现当图形化界面中指定的 Python 解释器不带有 pytorch 而 launch.json 中指定的 Python 解释器带有 pytorch，虽然代码运行还是选择了 launch.json 中的 Python 解释器但是在代码编辑器中提示代码信息的 Python 解释器依然为图形化界面中所指定的，如下的代码中在代码编辑器中提示 pytorch 并不存在。

为此我们可以得到两个结论：

\1. 在`launch.json`中指定 Python 解释器在代码执行时享有最高的权限，优于图形化界面中指定的 Python 解释器。

\2. 不论是否在`launch.json`中指定 Python 解释器，在代码编辑窗口中对代码信息进行信息提示、补全等操作时所选择的 Python 解释器依然为图形化界面中所指定的。

{% asset_img 010.png [image10] %}

=============================================

在 vscode 中创建 launch.json 更为简单的操作则是直接在主菜单中选择 运行和调试（也可以通过键盘操作，按键为：`ctrl+shift+D`），然后选择创建`launch.json`文件。

{% asset_img 011.png [image11] %}

​ 本博客是博主个人学习时的一些记录，不保证是为原创，个别文章加入了转载的源地址还有个别文章是汇总网上多份资料所成，在这之中也必有疏漏未加标注者，如有侵权请与博主联系。 如果未特殊标注的则为原创，遵循 CC 4.0 BY-SA 版权协议。
