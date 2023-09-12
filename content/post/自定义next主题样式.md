---
title: '自定义next主题样式'
description: '自定义next主题样式'
keywords: '自定义next主题样式'

date: 2022-08-27T00:57:00+08:00
lastmod: 2023-09-12T11:58:04+08:00

categories:
  - HEXO个人博客搭建
tags:
  - next主题
  - 自定义样式
author: 任浪漫
abbrlink: 3936651336
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
#url: "自定义next主题样式.html"
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

自定义 next 主题样式

<!--more-->

[自定义文件](https://theme-next.js.org/docs/advanced-settings/custom-files.html#Hide-Sidebar-on-Mobile)

[NextT 用户文档](https://theme-next.js.org/docs/) - [高级设置](https://theme-next.js.org/docs/advanced-settings/) - 自定义文件

<!--more-->

## 自定义文件支持

[拉取请求 #868](https://github.com/theme-next/hexo-theme-next/pull/868)调整了自定义布局或样式的方式，取消了原主题目录下的自定义文件（如`_custom/custom.styl`），只保留了指定自定义文件的方式**NexT config file**.

将自定义文件与主题文件分开是一个很好的做法，这样您就可以在不修改主题的原始源代码的情况下添加自定义内容，并避免由于`git merge`.而产生的冲突。

与[数据文件](https://hexo.io/docs/data-files)一样，您可以将所有自定义布局或样式放在特定的位置(例如:`hexo/source/_data`)。将自定义文件添加到`hexo/source/_data`中，并取消 NextT 配置文件中`custom_file_path`部分下的内容注释。

> `custom_file_path`中的文件名和路径必须保持一致。

NextT 配置文件

```yml
custom_file_path:
  #head: source/_data/head.njk
  #header: source/_data/header.njk
  #sidebar: source/_data/sidebar.njk
  #postMeta: source/_data/post-meta.njk
  #postBodyEnd: source/_data/post-body-end.njk
  #footer: source/_data/footer.njk
  #bodyEnd: source/_data/body-end.njk
  #variable: source/_data/variables.styl
  #mixin: source/_data/mixins.styl
  #style: source/_data/styles.styl
```

除`custom_file_path`之外，我们还提供了更灵活的自定义方式，您可以阅读[Theme Inject](https://theme-next.js.org/docs/advanced-settings/injects.html)文档中的内容。

## 修改布局示例

### Live2d 小部件

在站点根目录下创建`source/_data/head.njk`文件并编辑添加如下内容:
`hexo/source/_data/head.njk`

```js
<script src="https://fastly.jsdelivr.net/gh/stevenjoezhang/live2d-widget@latest/autoload.js">
  {' '}
</script>
```

然后取消**NexT 配置文件**中`custom_file_path`下的`head`注释
`NexT config file`

```yml
custom_file_path:
  head: source/_data/head.njk
```

### 侧边栏中的 Netlify 徽标

在站点根目录下创建`source/_data/sidebar.njk`文件并编辑添加如下内容:
`hexo/source/_data/sidebar.njk`

```js
<div class="cc-license animated" itemprop="sponsor">
  <a href="https://www.netlify.com" class="cc-opacity" title="Deploy with Netlify → https://www.netlify.com" target="_blank"><img width="80" src="https://www.netlify.com/img/global/badges/netlify-dark.svg" alt="Netlify"></a>
</div>
```

然后取消**NexT 配置文件**中`custom_file_path`部分下的`sidebar`部分的注释。
`NexT config file`

```yml
custom_file_path:
# 侧边栏
sidebar: source/_data/sidebar.njk
```

## 修改样式示例

### 标签云颜色

在站点根目录下创建`source/_data/variables.styl`文件并编辑添加如下内容:
`source/_data/variables.styl`

```stylus
$tag-cloud-start      = #aaa;
$tag-cloud-end        = #111;
$tag-cloud-start-dark = #555;
$tag-cloud-end-dark   = #eee;
```

然后取消**NexT 配置文件**中`custom_file_path`部分下的`variable`部分的注释。

`NexT config file`

```yml
custom_file_path:
  variable: source/_data/variables.styl
```

### 如何更改内容宽度

默认情况下，NextT 的内容宽度由以下变量控制：

- `$content-desktop`→ 当屏幕宽度 < 1200px。
- `$content-desktop-large`→ 当屏幕宽度 >= 1200 像素时。
- `$content-desktop-largest`→ 当屏幕宽度 >= 1600 像素时。
- 在移动/平板设备中，它将使用响应宽度。

`source/_data/variables.styl`您可以通过编辑来覆盖默认内容宽度站点根目录.

#### [缪斯/迷雾计划](https://theme-next.js.org/docs/advanced-settings/custom-files.html#change-content-width-1)

Muse 和 Mist 方案的默认变量定义为：

`next/source/css/_variables/base.styl`

```stylus
$content-desktop         = 700px
$content-desktop-large   = 800px
$content-desktop-largest = 900px
```

例如，您可以使用百分比值覆盖这些变量以增加内容宽度。在站点根目录下创建`source/_data/variables.styl`文件并编辑添加如下内容:
`hexo/source/_data/variables.styl`

```stylus
$content -desktop = 90%
$content -desktop-large = 90%
$content -desktop-largest = 90%
```

> 如果值以百分比为单位，则在打开侧边栏期间将动态减小内容宽度以由您定义的百分比。
> 但在标准行为中，侧边栏必须取代您自己的内容。
> 为了解决它，您可以在中指定内容宽度`em`：
>
> `hexo/source/_data/variables.styl`
>
> ```stylus
> $content -desktop = 50em
> $content -desktop-large = 55em
> $content -desktop-largest = 60em
> ```

然后取消 NexT 配置文件中`custom_file_path`部分下的`variable`注释。

`NexT config file`

```yml
custom_file_path:
  variable: source/_data/variables.styl
```

#### [双鱼座/双子座计划](https://theme-next.js.org/docs/advanced-settings/custom-files.html#change-content-width-2)

双鱼座（和双子座）方案的默认变量定义为：

`next/source/css/_variables/base.styl`

```stylus
$content -desktop = 'calc(100% - %s)' % unit ( $content -desktop- padding / 2 , 'px' )
$content -desktop-large = 1160px
$content -desktop-largest = 73%
```

> $content-desktop 默认情况下，此方案中的值是自动响应的。它也可以更改为任何值，但为了获得更好的内容可见性，建议保持原样。

在这种方案中，内容宽度被定义为最大值，并且已经平衡:如果桌面宽度更宽，那么内容宽度将更窄，以方便阅读。但是如果您想在更宽的桌面中实现更窄的内容宽度，下面是一个例子。
在站点根目录下创建并编辑`source/_data/ variable.styl`，并添加变量:

```stylus
hexo/source/_data/variables.styl
$content -desktop-large = 65em
$content -desktop-largest = 65%
```

事实上，Gemini 方案只是 Pisces 方案的一个分支，并进行了一些样式改进。
因此，几乎所有来自 Pisces 方案的部分变量也被导入到 Gemini 方案中。
因此，这些变量或样式的变化将适用于双鱼座和双子座方案。

然后取消 NexT 配置文件中`custom_file_path`部分下的`variable`注释。

`NexT config file`

```yml
custom_file_path:
  variable: source/_data/variables.styl
```

### 在移动设备上隐藏侧边栏

在站点根目录下创建并编辑`source/_data/styles.styl`，并添加变量:
`hexo/source/_data/styles.styl`

```stylus
+tablet-mobile() {
  .sidebar-toggle, .sidebar {
    display: none;
  }
}
```

然后取消 NexT 配置文件中`custom_file_path`部分下的`style`注释。

`NexT config file`

```yml
custom_file_path:
  style: source/_data/styles.styl
```

### 在存档页面中隐藏“继续发布”

在站点根目录下创建并编辑`source/_data/styles.styl`，并添加样式:

`hexo/source/_data/styles.styl`

```stylus
.archive .collection-title {
  display: none !important;
}
```

然后取消 NexT 配置文件中`custom_file_path`部分下的`style`注释。

`NexT config file`

```yml
custom_file_path:
  style: source/_data/styles.styl
```

[文档](https://theme-next.js.org/docs/) - [高级设置](https://theme-next.js.org/docs/advanced-settings/) 自定义文件
