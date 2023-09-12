---
title: 'Linux 查看软连接和硬链接'
description: 'linux-查看软连接和硬链接'
keywords: 'linux,查看软连接和硬链接'

date: 2022-08-26T11:48:00+08:00
lastmod: 2023-09-12T11:59:17+08:00

tags:
  - linux
  - 软连接
  - 硬链接
categories:
  - 随笔
author: 任浪漫
abbrlink: 1157754107
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
#url: "linux-查看软连接和硬链接.html"
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

[**linux 查看软连接和硬链接**](https://www.csdn.net/tags/MtTaYg3sMjU5MzYtYmxvZwO0O0OO0O0O.html)

**参考：** **[Linux 软连接和硬链接 - iTech - 博客园](https://www.cnblogs.com/itech/archive/2009/04/10/1433052.html)**

<!-- more -->

## **1、Linux 链接概念**

- Linux 链接分两种，一种被称为硬链接（Hard Link），另一种被称为符号链接（Symbolic Link）。默认情况下，使用 ln 命令不加参数创建硬链接，加 -s 参数则创建软链接。

### **硬链接**

- 硬链接即让多个不在或者同在一个目录下的文件名，同时能够修改同一个文件，其中一个修改后，所有与其有硬链接的文件都一起修改了。

### **软链接**

- 软链接也称之为符号链接（Symbolic Link）。这个文件包含了另一个文件的路径名。可以是任意文件或目录，可以链接不同文件系统的文件。软链接类似于 Windows 的快捷方式。

## **2、软硬链接测试**

```shell
 [root@user ~]#  touch f1        # 创建文件 f1
 [root@user ~]#  ln f1 f2        # 创建 f1 的一个硬链接文件f2
 [root@user ~]#  ln -s f1 f3      # 创建 f1 的一个软链接文件f3
 [root@user ~]#  ls -li           # -i参数显示文件的inode节点信息
 total 24
 17567 -rw-------. 1 root root 1115 Jan 9 2014 anaconda-ks.cfg
  175 -rw-r--r--. 1 root root 3486 Aug 18 2014 cloud-set-guest-password
  235 -rw-r--r--. 2 root root  0 Mar 14 12:18 f1
  235 -rw-r--r--. 2 root root  0 Mar 14 12:18 f2
  237 lrwxrwxrwx. 1 root root  2 Mar 14 12:14 f3 -> f1
   49 -rw-r--r--. 1 root root 8526 Jan 9 2014 install.log
   67 -rw-r--r--. 1 root root 3314 Jan 9 2014 install.log.syslog
```

通过上面的测试可以看出：硬链接文件 f2 与源文件 f1 的 **inode 节点相同**,均为 235，软链接 f3 则与两者的 **inode 节点不同**。

```shell
 [root@user ~]#  echo "I am f1" >> f1
 [root@user ~]#  cat f1
 I am f1
 [root@user ~]#  cat f2
 I am f1
 [root@user ~]#  cat f3
 I am f1
 [root@user ~]#  rm -f f1
 [root@user ~]#  cat f2
 I am f1
 [root@user ~]# cat f3
 cat: f3: No such file or directory
```

通过上面的测试可以看出：
当**删除原始文件 f1** 后，**硬链接 f2 不受影响**，但是**软链接 f3 文件失效**

## **3、小结**

- 硬链接相当于创建了源文件的副本，不会随着源文件的删除而消失，会随着源文件内容的更改而更改；

- 软链接相当于创建了源文件的快捷方式，会随着源文件的删除而失效；
