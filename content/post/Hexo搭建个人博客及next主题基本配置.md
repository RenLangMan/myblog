---
title: 'Hexo搭建个人博客及next主题基本配置'
description: 'Hexo搭建个人博客及next主题基本配置'
keywords: 'Hexo搭建个人博客及next主题基本配置'

date: 2022-08-25T11:20:00+08:00
lastmod: 2023-09-12T11:58:06+08:00

categories:
  - HEXO个人博客搭建
tags:
  - hexo博客搭建
  -
author: 任浪漫
abbrlink: 4246096149
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
#url: "hexo搭建个人博客及next主题基本配置.html"
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

[Hexo 搭建个人博客及 next 主题基本配置](https://www.cnblogs.com/starsray/p/12058361.html)

<!-- more -->

## 前言

国内一些免费的博客平台比如 CSDN、博客园都已经很成熟，功能齐全，已经可以满足我们的需求，帮助我们记录学习过程遇到的问题，还能分享帮助其他人解决问题。为什么还要自己动手去搭建博客呢？首先写博客是对自己学习经历的一种总结，其次搭建个人博客，是对自己独立思考能力、动手能力的提升，通过大量的百度 Google 以及查看官方 API 解决问题，会瞬间觉得整个人心情都好了。最后奉上我的真实感受，搭博客不管你是否爱学习，喜欢新事物，一定要有一颗抗折腾的心~~~

## Hexo 安装

### Hexo 简介

Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。（摘自官方文档）查看[官方文档](https://hexo.io/zh-cn/docs/),简单说，Hexo 就是通过 GitHub、Gitee 或者 Coding 等代码托管平台，将本地写好的页面发布到远程网站利用 GitHub Pages 访问。文章使用 Markdown 语法书写，根据提前配置好的模板文件进行样式渲染，生成静态页面，这里的静态与动态是指数据获取来源方式，动态网站是指数据从数据库获取并进行展示，静态是生成的 html 网页，数据是固定的，这样减少了数据交互，可以加快网站的访问效率。
而且 Hexo 还有大量的主题进行拓展配置，完全可以根据个人喜好配置，[主题官方网站](https://hexo.io/themes/)，目前 GitHub 上 Star 最高的是[next](https://theme-next.org/)主题，本文配置是基于 next 最新版本 nxet7 进行配置，关于 next6 的配置可以参考[GitHub](https://heconly.gitee.io/)，由于国内访问效果不佳，考虑搭建一个新的基于[Gitee](https://heconly.gitee.io/)的博客。

Hexo Star 排名靠前的 10 个主题：

- [iissnan/hexo-theme-next](https://github.com/iissnan/hexo-theme-next)， star 14157
- [litten/hexo-theme-yilia](https://github.com/litten/hexo-theme-yilia)， star 6213
- [TryGhost/Casper](https://github.com/TryGhost/Casper)， star 1625
- [wuchong/jacman](https://github.com/wuchong/jacman)， star 975
- [A-limon/pacman](https://github.com/A-limon/pacman)， star 558
- [kathyqian/crisp-ghost-theme](https://github.com/kathyqian/crisp-ghost-theme)， star 531
- [AlxMedia/hueman](https://github.com/presscustomizr/hueman)，star 508
- [daleanthony/uno](https://github.com/daleanthony/uno)，star 494
- [xiangming/landscape-plus](https://github.com/xiangming/landscape-plus)， star 490
- [orderedlist/modernist](https://github.com/orderedlist/modernist)， star 423

博客由 GitHub 搬家而来，排名请以实际为主

### 使用准备

Hexo 的使用是基于 node.js 和 Github 的，首先需要在本地安装 node 客户端，其次需要注册 Github 账号，创建一个远程项目发布的仓库。node 下载网址：官方网站，如果不想去官方，这里附上我的百度网盘资源：下载链接，提取码：8rp5。安装之后输入以下命令检测，查看 node 和 npm 版本

```undefined

node -v
npm -v
```

这里说一下什么时 npm,npm 其实是 node.js 的包管理工具（package manager）。为啥我们需要一个包管理工具呢？因为我们在 Node.js 上开发时，会用到很多别人写的 JavaScript 代码。如果我们要使用别人写的某个包，每次都根据名称搜索一下官方网站，下载代码，解压，再使用，非常繁琐。于是一个集中管理的工具应运而生：大家都把自己开发的模块打包后放到 npm 官网上，如果要使用，直接通过 npm 安装就可以直接用，不用管代码存在哪，应该从哪下载。引用一下廖大的话，也可以直接去原网页查看

关于 GitHub 账号的创建以及仓库的配置，我就不在赘述，可以参考廖大的官方网站，不用太多，只用看到如何创建一个远程仓库即可，需要注意的是在搭建博客时远程仓库的地址一定要写成 xxx.github.io，xxx 为你的 github 用户名，这样定义可以直接使用这个仓库当作域名进行访问，否则地址就会变成用户名.github.io/xxx,造成不必要的麻烦。

### 安装

准备工作做好之后 hexo 的安装很简单，执行命进行安装

```avrasm

npm install hexo-cli -g
```

然后再本地创建一个文件夹作为你的博客初始化目录，我建的为 Hexo，然后进入这个文件夹，鼠标右键，点击，Git Bash Here,当然你也可以在任意地方打开，执行 cd 命令跳转到这个博客文件夹，然后执行命令进行初始化

```csharp

hexo init
#执行结果
$ hexo init
INFO  Cloning hexo-starter to E:\ew
Cloning into 'E:\ew'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 71 (delta 0), reused 0 (delta 0), pack-reused 68
Unpacking objects: 100% (71/71), done.
Submodule 'themes/landscape' (https://github.com/hexojs/hexo-theme-landscape.git) registered for path 'themes/landscape'
Cloning into 'E:/ew/themes/landscape'...
remote: Enumerating objects: 16, done.
remote: Counting objects: 100% (16/16), done.
remote: Compressing objects: 100% (13/13), done.
remote: Total 893 (delta 3), reused 12 (delta 2), pack-reused 877
Receiving objects: 100% (893/893), 2.56 MiB | 567.00 KiB/s, done.
Resolving deltas: 100% (466/466), done.
Submodule path 'themes/landscape': checked out '73a23c51f8487cfcd7c6deec96ccc7543960d350'
INFO  Install dependencies
npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.8 (node_modules\fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.8: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})
added 421 packages from 504 contributors and audited 4697 packages in 19.502s
found 3 vulnerabilities (2 low, 1 moderate)
  run `npm audit fix` to fix them, or `npm audit` for details
INFO  Start blogging with Hexo!
```

你会发现你创建的文件夹多了以下内容，这就是你博客所需要的依赖环境

```mipsasm

#博客文件目录
node_modules #hexo 所依赖的node模块，插件
scaffolds
source   #文章的资源目录
themes   #hexo 的主题目录
.gitignore
_config.yml  #hexo根目录配置文件，接下来会细说
package.json
package-lock.json
```

本地预览

```undefined

hexo s
```

hexo 部署项目常用命令：

```csharp

hexo n "文章名称" == hexo new "文章名称" #新建文章
hexo p == hexo publish
hexo g == hexo generate #生成
hexo s == hexo server  #启动服务预览
hexo d == hexo deploy #部署
hexo clean   #清除缓存
```

## 基本配置

### Hexo 根目录配置文件\_config.yml

```yaml
# Hexo Configuration
## Docs: https://hexo.io/docs/configuration.html
## Source: https://github.com/hexojs/hexo/

# Site 站点基本配置
title: #网站标题
subtitle: #网站副标题
description: #网站描述
keywords: #全局文章关键字配置
author: #作者名称
language: #语言配置
timezone: #时区（可不配置）

# URL 项目部署配置
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: # 你的github URL
root: #项目发布目录
permalink: :year/:month/:day/:title/
permalink_defaults:

# Directory hexo 项目的目录结构，文章存储位置
source_dir: source
public_dir: public
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code
i18n_dir: :lang
skip_render:

# Writing
new_post_name: :title.md # File name of new posts
default_layout: post
titlecase: false # Transform title into titlecase
external_link: true # Open external links in new tab
filename_case: 0
render_drafts: false
post_asset_folder: false
relative_link: false
future: true
highlight:
  enable: true
  line_number: true
  auto_detect: false
  tab_replace:

# Home page setting
# path: Root path for your blogs index page. (default = '')
# per_page: Posts displayed per page. (0 = disable pagination)
# order_by: Posts order. (Order by date descending by default)
index_generator:
  path: ''
  per_page: 10
  order_by: -date

# Category & Tag
default_category: uncategorized
category_map:
tag_map:

# Date / Time format
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: YYYY-MM-DD
time_format: HH:mm:ss

# Pagination
## Set per_page to 0 to disable pagination
per_page: 10
pagination_dir: page

# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: next

# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repository: git@gitee.com:heconly/heconly.git
  branch: master

# hexo-neat 博文压缩
neat_enable: true
neat_html:
  enable: true
  exclude:
neat_css:
  enable: true
  exclude:
    - '**/*.min.css'
neat_js:
  enable: true
  mangle: true
  output:
  compress:
  exclude:
    - '**/*.min.js'
    - '**/jquery.fancybox.pack.js'
    - '**/index.js'
#symbol字数统计
symbols_count_time:
  symbols: true
  time: true
  total_symbols: true
  total_time: true
#LocalSearch
search:
  path: search.xml
  field: post
  format: html
  limit: 10000
#sitemap
Plugins:
  - hexo-generator-baidu-sitemap
  - hexo-generator-sitemap
baidusitemap:
  path: baidusitemap.xml
sitemap:
  path: sitemap.xml
#配置音乐播放器
aplayer:
  meting: true
```

### next 主题根目录配置文件\_config.yml

```yaml

# ---------------------------------------------------------------
# Theme Core Configuration Settings
# See: https://theme-next.org/docs/theme-settings/
# ---------------------------------------------------------------

# If false, merge configs from `_data/next.yml` into default configuration (rewrite).
# If true, will fully override default configuration by options from `_data/next.yml` (override). Only for NexT settings.
# And if true, all config from default NexT `_config.yml` must be copied into `next.yml`. Use if you know what you are doing.
# Useful if you want to comment some options from NexT `_config.yml` by `next.yml` without editing default config.
override: false

# Allow to cache content generation. Introduced in NexT v6.0.0.
cache:
  enable: true

# Redefine custom file paths. Introduced in NexT v6.0.2. If commented, will be used default custom file paths.
# For example, you want to put your custom styles file outside theme directory in root `source/_data`, set `styles: source/_data/styles.styl`
#custom_file_path:
  # Default paths: layout/_custom/*
  #head: source/_data/head.swig
  #header: source/_data/header.swig
  #sidebar: source/_data/sidebar.swig

  # Default path: source/css/_variables/custom.styl
  #variables: source/_data/variables.styl
  # Default path: source/css/_mixins/custom.styl
  #mixins: source/_data/mixins.styl
  # Default path: source/css/_custom/custom.styl
  #styles: source/_data/styles.styl


# ---------------------------------------------------------------
# Site Information Settings
# See: https://theme-next.org/docs/getting-started/
# ---------------------------------------------------------------

favicon:
  small: /images/favicon-16x16-next.png
  medium: /images/favicon-32x32-next.png
  apple_touch_icon: /images/apple-touch-icon-next.png
  safari_pinned_tab: /images/logo.svg
  #android_manifest: /images/manifest.json
  #ms_browserconfig: /images/browserconfig.xml

# Set rss to false to disable feed link.
# Leave rss as blank to use site's feed link, and install hexo-generator-feed: `npm install hexo-generator-feed --save`.
# Set rss to specific value if you have burned your feed already.
rss:
# 配置RSS
plugin:
- hexo-generator-feed
#Feed Atom
feed:
  #feed 类型 (atom/rss2)
  type: atom
  #rss 路径
  path: atom.xml
  #在 rss 中最多生成的文章数(0显示所有)
  limit: 20

# 设置footer
footer:
  # Specify the date when the site was setup. If not defined, current year will be used.
  #since: 2015

  # 设置footer底部样式中的icon和color
  # Icon between year and copyright info.
  icon:
    # Icon name in fontawesome, see: https://fontawesome.com/v4.7.0/icons/
    # `heart` is recommended with animation in red (#ff0000).
    name: user
    # If you want to animate the icon, set it to true.
    animated: false
    # Change the color of icon, using Hex Code.
    color: "#808080"

  # If not defined, `author` from Hexo main config will be used.
  copyright:设置你的copyright

  # 设置powerby样式
  powered:
    # Hexo link (Powered by Hexo).
    enable: true
    # Version info of Hexo after Hexo link (vX.X.X).
    version: true

  # 设置主题样式
  theme:
    # Theme & scheme info link (Theme - NexT.scheme).
    enable: true
    # Version info of NexT after scheme info (vX.X.X).
    version: true

  # Beian icp information for Chinese users. In China, every legal website should have a beian icp in website footer.
  # http://www.miitbeian.gov.cn
  beian:
    enable: false
    icp:

  # Any custom text can be defined here.
  #custom_text: Hosted by <a href="https://pages.coding.me" class="theme-link" rel="noopener" target="_blank">Coding Pages</a>

# Creative Commons 4.0 International License.
# See: https://creativecommons.org/share-your-work/licensing-types-examples
# Available values of license: by | by-nc | by-nc-nd | by-nc-sa | by-nd | by-sa | zero
# You can set a language value if you prefer a translated version of CC license.
# CC licenses are available in 39 languages, where you can find the specific and correct abbreviation you need.
# Valid values of language: deed.zh, deed.fr, deed.de, etc.
creative_commons:
  license: by-nc-sa
  sidebar: false
  post: true
  language:

# 博客右上角是否展示GitHub banner
# `Follow me on GitHub` banner in the top-right corner.
github_banner:
  enable: true
  permalink: https://github.com/Hconly
  title: Follow me on GitHub

# SEO优化
# ---------------------------------------------------------------
# SEO Settings
# ---------------------------------------------------------------

# Disable Baidu transformation on mobile devices.
disable_baidu_transformation: false

# Set a canonical link tag in your hexo, you could use it for your SEO of blog.
# See: https://support.google.com/webmasters/answer/139066
# Tips: Before you open this tag, remember set up your URL in hexo _config.yml (e.g. url: http://yourdomain.com)
canonical: true
# 是否启用SEO
# Change headers hierarchy on site-subtitle (will be main site description) and on all post / page titles for better SEO-optimization.
seo: false

# If true, will add site-subtitle to index page, added in main hexo config.
# subtitle: Subtitle
index_with_subtitle: false

# Automatically add external URL with BASE64 encrypt & decrypt.
exturl: false

# 设置Google搜索收录
# Google Webmaster tools verification.
# See: https://www.google.com/webmasters
google_site_verification: true

# 设置Bing搜索收录
# Bing Webmaster tools verification.
# See: https://www.bing.com/webmaster
#bing_site_verification:

# Yandex Webmaster tools verification.
# See: https://webmaster.yandex.ru
#yandex_site_verification:

# 设置百度搜索收录
# Baidu Webmaster tools verification.
# See: https://ziyuan.baidu.com/site
#baidu_site_verification:

# Enable baidu push so that the blog will push the url to baidu automatically which is very helpful for SEO.
baidu_push: false

# 主页菜单设置
# ---------------------------------------------------------------
# Menu Settings
# ---------------------------------------------------------------

# When running the site in a subdirectory (e.g. domain.tld/blog), remove the leading slash from link value (/archives -> archives).
# Usage: `Key: /link/ || icon`
# Key is the name of menu item. If the translation for this item is available, the translated text will be loaded, otherwise the Key name will be used. Key is case-senstive.
# Value before `||` delimeter is the target link.
# Value after `||` delimeter is the name of FontAwesome icon. If icon (with or without delimeter) is not specified, question icon will be loaded.
# External url should start with http:// or https://
# 需要展示的菜单项，#注释不显示，后面为菜单对应的页面，如果添加菜单可以用命令 hexo new page 'page_name',再添加一列即可添加一个新的菜单项
menu:
  home: / || home
  categories: /categories/ || th
  archives: /archives/ || archive
  tags: /tags/ || tags
  about: /about/ || user
  #schedule: /schedule/ || calendar
  #sitemap: /sitemap.xml || sitemap
  #commonweal: /404/ || heartbeat

# 是否展示菜单icon图标
# Enable / Disable menu icons / item badges.
menu_settings:
  icons: true
  badges: false


# ---------------------------------------------------------------
# Scheme Settings
# ---------------------------------------------------------------

# 选择next主题下的风格，共支持四种风格，简洁/酷炫,具体选择可根据爱好选择，选择后重新部署，或者hexo s在本地预览
# Schemes
scheme: Mist
#scheme: Mist
#scheme: Pisces
#scheme: Gemini

# 侧边栏设置
# ---------------------------------------------------------------
# Sidebar Settings
# See: https://theme-next.org/docs/theme-settings/sidebar
# ---------------------------------------------------------------

# 侧边栏需要展示的链接，博客内部链接，文章、归档等是否显示
# Posts / Categories / Tags in sidebar.
site_state: true

# 添加外部链接，可添加友链，博客等等，||后面可以指定图标，图标样式可以去next主题网站查看选择
# Social Links
# Usage: `Key: permalink || icon`
# Key is the link label showing to end users.
# Value before `||` delimeter is the target permalink.
# Value after `||` delimeter is the name of FontAwesome icon. If icon (with or without delimeter) is not specified, globe icon will be loaded.
social:
  GitHub: https://github.com/Hconly || github
  E-Mail: 3344758676@qq.com || envelope
  BLog: https://www.cnblogs.com/conly/ ||
  Link: https://www.conly.top ||
  #Google: https://plus.google.com/yourname || google
  #Twitter: https://twitter.com/yourname || twitter
  #FB Page: https://www.facebook.com/yourname || facebook
  #VK Group: https://vk.com/yourname || vk
  #StackOverflow: https://stackoverflow.com/yourname || stack-overflow
  #YouTube: https://youtube.com/yourname || youtube
  #Instagram: https://instagram.com/yourname || instagram
  #Skype: skype:yourname?call|chat || skype

social_icons:
  enable: true
  icons_only: false
  transition: true

# Blog rolls
links_icon: link
links_title: Links
links_layout: block
#links_layout: inline
links:
  #Title: http://example.com

# Sidebar Avatar
avatar:
  # In theme directory (source/images): /images/avatar.gif
  # In site directory (source/uploads): /uploads/avatar.gif
  # You can also use other linking images.
  url: /images/avatar.jpg
  # If true, the avatar would be dispalyed in circle.
  rounded: true
  # The value of opacity should be choose from 0 to 1 to set the opacity of the avatar.
  opacity: 1
  # If true, the avatar would be rotated with the cursor.
  rotated: true

# 文章内容设置 enable显示文章目录，具体设置根据个人习惯选择下面的具体选项
# Table Of Contents in the Sidebar
toc:
  enable: true
  # Automatically add list number to toc.
  number: true
  # If true, all words will placed on next lines if header width longer then sidebar width.是否自适应换行
  wrap: false
  # If true, all level of TOC in a post will be displayed, rather than the activated part of it.
  expand_all: false
  # Maximum heading depth of generated toc. You can set it in one post through `toc_max_depth` in Front Matter.
  max_depth: 6

# 侧边栏位置，不同next的schema可选择位置不一样，可参考下面样例
sidebar:
  # Sidebar Position, available values: left | right (only for Pisces | Gemini).
  position: left
  #position: right

  # Manual define the sidebar width. If commented, will be default for:
  # Muse | Mist: 320
  # Pisces | Gemini: 240
  #width: 300

  # Sidebar Display, available values (only for Muse | Mist):
  #  - post    expand on posts automatically. Default.
  #  - always  expand for all pages automatically.
  #  - hide    expand only when click on the sidebar toggle icon.
  #  - remove  totally remove sidebar including sidebar toggle.
  display: post

  # Sidebar offset from top menubar in pixels (only for Pisces | Gemini).
  offset: 12
  # Enable sidebar on narrow view (only for Muse | Mist).
  onmobile: true
  # Click any blank part of the page to close sidebar (only for Muse | Mist).
  dimmer: true

# 返回顶部按钮，是否展示，可以设置是否显示阅读百分比
back2top:
  enable: true
  # Back to top in sidebar.
  sidebar: false
  # Scroll percent label in b2t button.
  scrollpercent: true

# 添加聊天窗口，需要选择相应的服务
# A button to open designated chat widget in sidebar.
# Firstly, you need enable the chat service you want to activate its sidebar button.
chat:
  enable: false
  #service: chatra
  #service: tidio
  icon: comment # icon in Font Awesome 4, set false to disable icon
  text: Chat # button text, change it as you wish

# 文章设置
# ---------------------------------------------------------------
# Post Settings
# See: https://theme-next.org/docs/theme-settings/posts
# ---------------------------------------------------------------

# Set the text alignment in the posts.
text_align:
  # Available values: start | end | left | right | center | justify | justify-all | match-parent
  desktop: justify
  mobile: justify
# 如果需要折叠在折叠的地方添加<!--mored-->标志
# Automatically scroll page to section which is under <!-- more --> mark.
scroll_to_more: true

# Automatically saving scroll position on each post / page in cookies.
save_scroll: false

# Automatically excerpt description in homepage as preamble text.
excerpt_description: true

# Automatically Excerpt (Not recommend).
# Use <!-- more --> in the post to control excerpt accurately.
auto_excerpt:
  enable: true
  length: 100

# Read more button
# If true, the read more button would be displayed in excerpt section.
read_more_btn: true

# Post meta display settings
post_meta:
  item_text: true
  created_at: true
  updated_at:
    enable: true
    another_day: true
  categories: true

# Post wordcount display settings
# Dependencies: https://github.com/theme-next/hexo-symbols-count-time
symbols_count_time:
  separated_meta: false
  item_text_post: true
  item_text_total: true
  awl: 4
  wpm: 275

# 代码块样式设置
codeblock:
  # Manual define the border radius in codeblock, leave it blank for the default value: 1
  border_radius: 1
  # Add copy button on codeblock
  copy_button:
    enable: true
    # Show text copy result
    show_result: true
    # Style: only 'flat' is currently available, leave it blank if you prefer default theme
    style: flat

# Wechat Subscriber
wechat_subscriber:
  #enable: true
  #qcode: /path/to/your/wechatqcode e.g. /uploads/wechat-qcode.jpg
  #description: e.g. subscribe to my blog by scanning my public wechat account

# 打赏功能
# Reward (Donate)
reward_settings:
  # If true, reward would be displayed in every article by default.
  # You can show or hide reward in a specific article throuth `reward: true | false` in Front Matter.
  enable: true
  animation: true
  #comment: Donate comment here
# 添加你的微信/支付宝收款码图片
reward:
  wechatpay: /images/wechatpay.png
  alipay: /images/alipay.png
  #bitcoin: /images/bitcoin.png

# Related popular posts
# Dependencies: https://github.com/tea3/hexo-related-popular-posts
related_posts:
  enable: false
  title: # custom header, leave empty to use the default one
  display_in_home: false
  params:
    maxCount: 5
    #PPMixingRate: 0.0
    #isDate: false
    #isImage: false
    #isExcerpt: false

# Post edit
# Dependencies: https://github.com/hexojs/hexo-deployer-git
post_edit:
  enable: false
  url: https://github.com/user-name/repo-name/tree/branch-name/subdirectory-name # Link for view source.
  #url: https://github.com/user-name/repo-name/edit/branch-name/subdirectory-name # Link for fork & edit.


# ---------------------------------------------------------------
# Misc Theme Settings
# ---------------------------------------------------------------

# Reduce padding / margin indents on devices with narrow width.
mobile_layout_economy: true

# Android Chrome header panel color ($brand-bg / $headband-bg => $black-deep).
android_chrome_color: "#222"

# Hide sticky headers and color the menu bar on Safari (iOS / macOS).
safari_rainbow: false

# Optimize the display of scrollbars on webkit based browsers.
custom_scrollbar: false

# Custom Logo
# Do not support Scheme Mist currently.
custom_logo:
  enable: false
  image: #/uploads/custom-logo.jpg

# Code Highlight theme
# Available values: normal | night | night eighties | night blue | night bright
# https://github.com/chriskempson/tomorrow-theme
highlight_theme: normal

# Enable "cheers" for archive page.
cheers: true

# TagCloud settings for tags page.
tagcloud:
  # If true, font size, font color and amount of tags can be customized
  enable: false
  # All values below are same as default, change them by yourself
  min: 12 # min font size in px
  max: 30 # max font size in px
  start: "#ccc" # start color (hex, rgba, hsla or color keywords)
  end: "#111" # end color (hex, rgba, hsla or color keywords)
  amount: 200 # amount of tags, chage it if you have more than 200 tags

# ---------------------------------------------------------------
# Font Settings. Introduced in NexT v5.0.1.
# Find fonts on Google Fonts (https://www.google.com/fonts)
# All fonts set here will have the following styles:
#   light, light italic, normal, normal italic, bold, bold italic
# Be aware that setting too much fonts will cause site running slowly
# ---------------------------------------------------------------
# To avoid space between header and sidebar in scheme Pisces / Gemini, Web Safe fonts are recommended for `global` (and `logo`):
# Arial | Tahoma | Helvetica | Times New Roman | Courier New | Verdana | Georgia | Palatino | Garamond | Comic Sans MS | Trebuchet MS
# ---------------------------------------------------------------

font:
  enable: false

  # Uri of fonts host, e.g. //fonts.googleapis.com (Default).
  host:

  # Font options:
  # `external: true` will load this font family from `host` above.
  # `family: Times New Roman`. Without any quotes.
  # `size: xx`. Use `px` as unit.

  # Global font settings used for all elements in <body>.
  global:
    external: true
    family: Lato
    size:

  # Font settings for Headlines (H1, H2, H3, H4, H5, H6).
  # Fallback to `global` font settings.
  headings:
    external: true
    family:
    size:

  # Font settings for posts.
  # Fallback to `global` font settings.
  posts:
    external: true
    family:

  # Font settings for Logo.
  # Fallback to `global` font settings.
  logo:
    external: true
    family:
    size:

  # Font settings for <code> and code blocks.
  codes:
    external: true
    family:
    size:

# ---------------------------------------------------------------
# Third Party Services Settings
# See: https://theme-next.org/docs/third-party-services/
# You may need to install dependencies or set CDN URLs in `vendors`
# There are two different CDN providers by default:
#   - jsDelivr (cdn.jsdelivr.net), works everywhere even in China
#   - CDNJS (cdnjs.cloudflare.com), provided by cloudflare
# ---------------------------------------------------------------

# Math Equations Render Support
math:
  enable: false

  # Default (true) will load mathjax / katex script on demand.
  # That is it only render those page which has `mathjax: true` in Front Matter.
  # If you set it to false, it will load mathjax / katex srcipt EVERY PAGE.
  per_page: true

  engine: mathjax
  #engine: katex

  # hexo-rendering-pandoc (or hexo-renderer-kramed) needed to full MathJax support.
  mathjax:
    cdn: //cdn.jsdelivr.net/npm/mathjax@2/MathJax.js?config=TeX-AMS-MML_HTMLorMML
    #cdn: //cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML

    # See: https://mhchem.github.io/MathJax-mhchem/
    #mhchem: //cdn.jsdelivr.net/npm/mathjax-mhchem@3
    #mhchem: //cdnjs.cloudflare.com/ajax/libs/mathjax-mhchem/3.3.0

  # hexo-renderer-markdown-it-plus (or hexo-renderer-markdown-it with markdown-it-katex plugin) needed to full Katex support.
  katex:
    cdn: //cdn.jsdelivr.net/npm/katex@0/dist/katex.min.css
    #cdn: //cdnjs.cloudflare.com/ajax/libs/KaTeX/0.7.1/katex.min.css

    copy_tex:
      # See: https://github.com/KaTeX/KaTeX/tree/master/contrib/copy-tex
      enable: false
      copy_tex_js: //cdn.jsdelivr.net/npm/katex@0/dist/contrib/copy-tex.min.js
      copy_tex_css: //cdn.jsdelivr.net/npm/katex@0/dist/contrib/copy-tex.min.css

# Han Support
# Dependencies: https://github.com/theme-next/theme-next-han
han: false

# Pangu Support
# Dependencies: https://github.com/theme-next/theme-next-pangu
# For more information: https://github.com/vinta/pangu.js
pangu: false

# Quicklink Support
# Dependencies: https://github.com/theme-next/theme-next-quicklink
# Visit https://github.com/GoogleChromeLabs/quicklink for details
quicklink:
  enable: false

  # Quicklink (quicklink.umd.js script) is loaded on demand
  # Add `quicklink: true` in Front Matter of the page or post you need
  # Home page and archive page can be controlled through home and archive options below
  home: true
  archive: true

  # Default (true) will initialize quicklink after the load event fires
  delay: true
  # Custom a time in milliseconds by which the browser must execute prefetching
  timeout: 3000
  # Default (true) will enable fetch() or falls back to XHR
  priority: true

  # For more flexibility you can add some patterns (RegExp, Function, or Array) to ignores
  # See: https://github.com/GoogleChromeLabs/quicklink#custom-ignore-patterns
  # Leave ignores as empty if you don't understand what it means
  # Example:
  # ignores:
  #   - /\/api\/?/
  #   - uri => uri.includes('.xml')
  #   - (uri, el) => el.hasAttribute('noopener')
  ignores:

# Bookmark Support
# Dependencies: https://github.com/theme-next/theme-next-bookmark
bookmark:
  enable: false
  # If auto, save the reading position when closing the page or clicking the bookmark-icon.
  # If manual, only save it by clicking the bookmark-icon.
  save: auto

# Reading progress bar
# Dependencies: https://github.com/theme-next/theme-next-reading-progress
reading_progress:
  enable: false
  color: "#37c6c0"
  height: 2px

# Google Calendar
# Share your recent schedule to others via calendar page.
# API Documentation: https://developers.google.com/google-apps/calendar/v3/reference/events/list
# To get api_key: https://console.developers.google.com
# Create & manage a public Google calendar: https://support.google.com/calendar/answer/37083
calendar:
  enable: false
  calendar_id: <required> # Your Google account E-Mail
  api_key: <required>
  orderBy: startTime
  offsetMax: 24 # Time Range
  offsetMin: 4 # Time Range
  showDeleted: false
  singleEvents: true
  maxResults: 250

# 评论插件 推荐Gitment或者Gittalk,具体设置方法可以百度一下
# ---------------------------------------------------------------
# Comments and Widgets
# See: https://theme-next.org/docs/third-party-services/comments-and-widgets
# ---------------------------------------------------------------

# Disqus
disqus:
  enable: false
  shortname:
  count: false
  lazyload: false

# DisqusJS
# Alternative Disqus - Render comment component using Disqus API
# Demo: https://suka.js.org/DisqusJS/
disqusjs:
  enable: false
  # API Endpoint of Disqus API (https://disqus.com/api/)
  # leave api empty if you are able to connect to Disqus API
  # otherwise you need a reverse proxy for Disqus API
  # For example:
  # api: https://disqus.skk.moe/disqus/
  api:
  apikey: # register new application from https://disqus.com/api/applications/
  shortname: # See: https://disqus.com/admin/settings/general/

# Changyan
changyan:
  enable: false
  appid:
  appkey:

# Valine
# You can get your appid and appkey from https://leancloud.cn
# More info available at https://valine.js.org
valine:
  enable: false # When enable is set to be true, leancloud_visitors is recommended to be closed for the re-initialization problem within different leancloud adk version.
  appid:  # your leancloud application appid
  appkey:  # your leancloud application appkey
  notify: false # mail notifier, See: https://github.com/xCss/Valine/wiki
  verify: false # Verification code
  placeholder: Just go go # comment box placeholder
  avatar: mm # gravatar style
  guest_info: nick,mail,link # custom comment header
  pageSize: 10 # pagination size
  language: zh-CN
  visitor: false # leancloud-counter-security is not supported for now. When visitor is set to be true, appid and appkey are recommended to be the same as leancloud_visitors' for
  counter compatibility. Article reading statistic https://valine.js.org/visitor.html
  comment_count: true # if false, comment count will only be displayed in post page, not in home page

# LiveRe comments system
# You can get your uid from https://livere.com/insight/myCode (General web site)
#livere_uid: your uid

# Gitment
# Introduction: https://github.com/imsun/gitment
gitment:
  enable: false
  mint: false
  count: false
  lazy: false
  cleanly: false
  language: # Force language, or auto switch by theme
  github_user: hconly
  github_repo: gitment-comments
  client_id: your client_id
  client_secret: your client_secret
  proxy_gateway: # Address of api proxy, See: https://github.com/aimingoo/intersect
  redirect_protocol: # Protocol of redirect_uri with force_redirect_protocol when mint enabled

# Gitalk
# Demo: https://gitalk.github.io
gitalk:
  enable: true
  github_id: Hconly
  repo: gittalk-comments
  client_id: your client_id
  client_secret: your client_secret
  admin_user: Hconly
  distraction_free_mode: true
  # Gitalk's display language depends on user's browser or system environment
  # If you want everyone visiting your site to see a uniform language, you can set a force language value
  # Available values: en, es-ES, fr, ru, zh-CN, zh-TW
  language: en

# 分享模块 推荐使用百度分享
# ---------------------------------------------------------------
# Content Sharing Services
# See: https://theme-next.org/docs/third-party-services/content-sharing-services
# ---------------------------------------------------------------

# Baidu Share
# Available values: button | slide
# Warning: Baidu Share does not support https.
#baidushare:
##  type: button

# AddThis Share, See: https://www.addthis.com
# Go to https://www.addthis.com/dashboard to customize your tools.
#add_this_id:

# Likely Share
# See: https://ilyabirman.net/projects/likely/
# Likely supports four looks, nine social networks, any button text
# You are free to modify the text value and order of any network
likely:
  enable: false
  look: normal # available values: normal, light, small, big
  networks:
    twitter: Tweet
    facebook: Share
    linkedin: Link
    gplus: Plus
    vkontakte: Share
    odnoklassniki: Class
    telegram: Send
    whatsapp: Send
    pinterest: Pin

# NeedMoreShare2
# Dependencies: https://github.com/theme-next/theme-next-needmoreshare2
# iconStyle: default | box
# boxForm: horizontal | vertical
# position: top / middle / bottom + Left / Center / Right
# networks:
# Weibo,Wechat,Douban,QQZone,Twitter,Facebook,Linkedin,Mailto,Reddit,Delicious,StumbleUpon,Pinterest,
# GooglePlus,Tumblr,GoogleBookmarks,Newsvine,Evernote,Friendfeed,Vkontakte,Odnoklassniki,Mailru
needmoreshare2:
  enable: false
  postbottom:
    enable: false
    options:
      iconStyle: box
      boxForm: horizontal
      position: bottomCenter
      networks: Weibo,Wechat,Douban,QQZone,Twitter,Facebook
  float:
    enable: false
    options:
      iconStyle: default
      boxForm: vertical
      position: middleRight
      networks: Wechat,QQZone,Weibo
# 文章分析 文章的字数，阅读时间，访客数，阅读数设置等 推荐busuanzi_count，需要注册账号，按照引导来设置
# ---------------------------------------------------------------
# Statistics and Analytics
# See: https://theme-next.org/docs/third-party-services/statistics-and-analytics
# ---------------------------------------------------------------

# Baidu Analytics ID
#baidu_analytics:

# Growingio Analytics ID
# Copyright 2015-2018 GrowingIO, Inc. More info available at https://www.growingio.com
#growingio_analytics: #your projectId

# Google Analytics
#google_analytics:
#  tracking_id:
#  localhost_ignored: true

# CNZZ count
#cnzz_siteid:

# Application Insights
# See: https://azure.microsoft.com/en-us/services/application-insights
#application_insights:

# Post widgets & FB/VK comments settings.
# ---------------------------------------------------------------
# Facebook SDK Support
facebook_sdk:
  enable:       false
  app_id:       #<app_id>
  fb_admin:     #<user_id>
  like_button:  #true
  webmaster:    #true

# Facebook comments plugin
# This plugin depends on Facebook SDK.
# If facebook_sdk.enable is false, Facebook comments plugin is unavailable.
facebook_comments_plugin:
  enable:       false
  num_of_posts: 10    # min posts num is 1
  width:        100%  # default width is 550px
  scheme:       light # default scheme is light (light or dark)

# VKontakte API Support
# To get your AppID visit https://vk.com/editapp?act=create
vkontakte_api:
  enable:       false
  app_id:       #<app_id>
  like:         true
  comments:     true
  num_of_posts: 10

# Star rating support to each article.
# To get your ID visit https://widgetpack.com
rating:
  enable: false
  id:     #<app_id>
  color:  fc6423
# ---------------------------------------------------------------

# Show number of visitors to each article.
# You can visit https://leancloud.cn to get AppID and AppKey.
leancloud_visitors:
  enable: false
  app_id: #<app_id>
  app_key: #<app_key>
  # Dependencies: https://github.com/theme-next/hexo-leancloud-counter-security
  # If you don't care about security in leancloud counter and just want to use it directly
  # (without hexo-leancloud-counter-security plugin), set `security` to `false`.
  security: true
  betterPerformance: false

# Another tool to show number of visitors to each article.
# Visit https://console.firebase.google.com/u/0/ to get apiKey and projectId.
# Visit https://firebase.google.com/docs/firestore/ to get more information about firestore.
firestore:
  enable: false
  collection: articles #required, a string collection name to access firestore database
  apiKey: #required
  projectId: #required
  bluebird: false #enable this if you want to include bluebird 3.5.1(core version) Promise polyfill

# Show Views / Visitors of the website / page with busuanzi.
# Get more information on http://ibruce.info/2015/04/04/busuanzi
busuanzi_count:
  enable: true
  total_visitors: true
  total_visitors_icon: user
  total_views: true
  total_views_icon: eye
  post_views: true
  post_views_icon: eye
  site_uv: true
  site_pv: true
  page_pv: true

# Tencent analytics ID
#tencent_analytics:

# Tencent MTA ID
#tencent_mta:

# ---------------------------------------------------------------
# Search Services
# See: https://theme-next.org/docs/third-party-services/search-services
# ---------------------------------------------------------------

# Algolia Search
# See: https://theme-next.org/docs/third-party-services/search-services#Algolia-Search
# Dependencies: https://github.com/theme-next/theme-next-algolia-instant-search
algolia_search:
  enable: false
  hits:
    per_page: 10
  labels:
    input_placeholder: Search for Posts
    hits_empty: "We didn't find any results for the search: ${query}"
    hits_stats: "${hits} results found in ${time} ms"

# Local search
# Dependencies: https://github.com/theme-next/hexo-generator-searchdb
local_search:
  enable: true
  # If auto, trigger search by changing input.
  # If manual, trigger search by pressing enter key or search button.
  trigger: auto
  # Show top n results per article, show all results by setting to -1
  top_n_per_article: 1
  # Unescape html strings to the readable one.
  unescape: false

# Swiftype Search API Key
#swiftype_key:

# ---------------------------------------------------------------
# Chat Services
# See: https://theme-next.org/docs/third-party-services/chat-services
# ---------------------------------------------------------------

# Chatra Support
# See: https://chatra.io
# Dashboard: https://app.chatra.io/settings/general
chatra:
  enable: false
  async: true
  id: # visit Dashboard to get your ChatraID
  #embed: # unfinished experimental feature for developers, See: https://chatra.io/help/api/#injectto

# Tidio Support
# See: https://www.tidiochat.com
# Dashboard: https://www.tidiochat.com/panel/dashboard
tidio:
  enable: false
  key: # Public Key, get it from Dashboard, See: https://www.tidiochat.com/panel/settings/developer

# 标签设置
# ---------------------------------------------------------------
# Tags Settings
# See: https://theme-next.org/docs/tag-plugins/
# ---------------------------------------------------------------

# Note tag (bs-callout)
note:
  # Note tag style values:
  #  - simple    bs-callout old alert style. Default.
  #  - modern    bs-callout new (v2-v3) alert style.
  #  - flat      flat callout style with background, like on Mozilla or StackOverflow.
  #  - disabled  disable all CSS styles import of note tag.
  style: simple
  icons: true
  border_radius: 3
  # Offset lighter of background in % for modern and flat styles (modern: -12 | 12; flat: -18 | 6).
  # Offset also applied to label tag variables. This option can work with disabled note tag.
  light_bg_offset: 0

# Tabs tag
tabs:
  enable: true
  transition:
    tabs: false
    labels: true
  border_radius: 0

# PDF tag, requires two plugins: pdfObject and pdf.js
# pdfObject will try to load pdf files natively, if failed, pdf.js will be used.
# The following `cdn` setting is only for pdfObject, because cdn for pdf.js might be blocked by CORS policy.
# So, you must install the dependency of pdf.js if you want to use pdf tag and make it available to all browsers.
# See: https://github.com/theme-next/theme-next-pdf
pdf:
  enable: false
  # Default height
  height: 500px
  pdfobject:
    cdn: //cdn.jsdelivr.net/npm/pdfobject@2/pdfobject.min.js
    #cdn: //cdnjs.cloudflare.com/ajax/libs/pdfobject/2.1.1/pdfobject.min.js

# Mermaid tag
mermaid:
  enable: false
  # Available themes: default | dark | forest | neutral
  theme: forest
  #cdn: //cdn.jsdelivr.net/npm/mermaid@8/dist/mermaid.min.js
  cdn: //cdnjs.cloudflare.com/ajax/libs/mermaid/8.0.0/mermaid.min.js

# 博客动画效果设置
# ---------------------------------------------------------------
# Animation Settings
# ---------------------------------------------------------------
# Use velocity to animate everything.
motion:
  enable: true
  async: false
  transition:
    # Transition variants:
    # fadeIn | fadeOut | flipXIn | flipXOut | flipYIn | flipYOut | flipBounceXIn | flipBounceXOut | flipBounceYIn | flipBounceYOut
    # swoopIn | swoopOut | whirlIn | whirlOut | shrinkIn | shrinkOut | expandIn | expandOut
    # bounceIn | bounceOut | bounceUpIn | bounceUpOut | bounceDownIn | bounceDownOut | bounceLeftIn | bounceLeftOut | bounceRightIn | bounceRightOut
    # slideUpIn | slideUpOut | slideDownIn | slideDownOut | slideLeftIn | slideLeftOut | slideRightIn | slideRightOut
    # slideUpBigIn | slideUpBigOut | slideDownBigIn | slideDownBigOut | slideLeftBigIn | slideLeftBigOut | slideRightBigIn | slideRightBigOut
    # perspectiveUpIn | perspectiveUpOut | perspectiveDownIn | perspectiveDownOut | perspectiveLeftIn | perspectiveLeftOut | perspectiveRightIn | perspectiveRightOut
    post_block: fadeIn
    post_header: slideDownIn
    post_body: slideDownIn
    coll_header: slideLeftIn
    # Only for Pisces | Gemini.
    sidebar: slideUpIn

# Fancybox. There is support for old version 2 and new version 3.
# Choose only one variant, do not need to install both.
# To install 2.x: https://github.com/theme-next/theme-next-fancybox
# To install 3.x: https://github.com/theme-next/theme-next-fancybox3
fancybox: true

# Polyfill to remove click delays on browsers with touch UIs.
# Dependencies: https://github.com/theme-next/theme-next-fastclick
fastclick: true

# Vanilla JavaScript plugin for lazyloading images.
# Dependencies: https://github.com/theme-next/theme-next-jquery-lazyload
lazyload: false

# Progress bar in the top during page loading.
# Dependencies: https://github.com/theme-next/theme-next-pace
pace: true
# Themes list:
# pace-theme-big-counter | pace-theme-bounce | pace-theme-barber-shop | pace-theme-center-atom
# pace-theme-center-circle | pace-theme-center-radar | pace-theme-center-simple | pace-theme-corner-indicator
# pace-theme-fill-left | pace-theme-flash | pace-theme-loading-bar | pace-theme-mac-osx | pace-theme-minimal
pace_theme: pace-theme-bounce
# canvas画布 整个博客背景效果
# Canvas-nest
# Dependencies: https://github.com/theme-next/theme-next-canvas-nest
canvas_nest:
  enable: true
  onmobile: true
  color: "186,85,211"
  opacity: 0.5
  zIndex: -1
  count: 99

# JavaScript 3D library.
# Dependencies: https://github.com/theme-next/theme-next-three
# three_waves
three_waves: false
# canvas_lines
canvas_lines: false
# canvas_sphere
canvas_sphere: false

# Canvas-ribbon
# Dependencies: https://github.com/theme-next/theme-next-canvas-ribbon
# size: The width of the ribbon.
# alpha: The transparency of the ribbon.
# zIndex: The display level of the ribbon.
canvas_ribbon:
  enable: false
  size: 150
  alpha: 0.5
  zIndex: -1

# 下面操作不要修改，除非你明白自己所做的修改
#! ---------------------------------------------------------------
#! DO NOT EDIT THE FOLLOWING SETTINGS
#! UNLESS YOU KNOW WHAT YOU ARE DOING
#! See: https://theme-next.org/docs/advanced-settings
#! ---------------------------------------------------------------

# Script Vendors. Set a CDN address for the vendor you want to customize.
# For example
#   jquery: https://ajax.googleapis.com/ajax/libs/jquery/2.2.0/jquery.min.js
# Be aware that you would better use the same version as internal ones to avoid potential problems.
# Please use the https protocol of CDN files when you enable https on your site.
vendors:
  # Internal path prefix. Please do not edit it.
  _internal: lib

  # Internal version: 2.1.3
  # Example:
  # jquery: //cdn.jsdelivr.net/npm/jquery@2/dist/jquery.min.js
  # jquery: //cdnjs.cloudflare.com/ajax/libs/jquery/2.1.3/jquery.min.js
  jquery:

  # Internal version: 2.1.5 & 3.5.7
  # See: https://fancyapps.com/fancybox
  # Example:
  # fancybox: //cdn.jsdelivr.net/gh/fancyapps/fancybox@3/dist/jquery.fancybox.min.js
  # fancybox: //cdnjs.cloudflare.com/ajax/libs/fancybox/3.5.6/jquery.fancybox.min.js
  # fancybox_css: //cdn.jsdelivr.net/gh/fancyapps/fancybox@3/dist/jquery.fancybox.min.css
  # fancybox_css: //cdnjs.cloudflare.com/ajax/libs/fancybox/3.5.6/jquery.fancybox.min.css
  fancybox:
  fancybox_css:

  # Internal version: 1.0.6
  # See: https://github.com/ftlabs/fastclick
  # Example:
  # fastclick: //cdn.jsdelivr.net/npm/fastclick@1/lib/fastclick.min.js
  # fastclick: //cdnjs.cloudflare.com/ajax/libs/fastclick/1.0.6/fastclick.min.js
  fastclick:

  # Internal version: 1.9.7
  # See: https://github.com/tuupola/jquery_lazyload
  # Example:
  # lazyload: //cdn.jsdelivr.net/npm/jquery-lazyload@1/jquery.lazyload.min.js
  # lazyload: //cdnjs.cloudflare.com/ajax/libs/jquery_lazyload/1.9.7/jquery.lazyload.min.js
  lazyload:

  # Internal version: 1.2.1
  # See: http://velocityjs.org
  # Example:
  # velocity: //cdn.jsdelivr.net/npm/velocity-animate@1/velocity.min.js
  # velocity: //cdnjs.cloudflare.com/ajax/libs/velocity/1.2.1/velocity.min.js
  # velocity_ui: //cdn.jsdelivr.net/npm/velocity-animate@1/velocity.ui.min.js
  # velocity_ui: //cdnjs.cloudflare.com/ajax/libs/velocity/1.2.1/velocity.ui.min.js
  velocity:
  velocity_ui:

  # Internal version: 4.6.2
  # See: https://fontawesome.com
  # Example:
  # fontawesome: //cdn.jsdelivr.net/npm/font-awesome@4/css/font-awesome.min.css
  # fontawesome: //cdnjs.cloudflare.com/ajax/libs/font-awesome/4.6.2/css/font-awesome.min.css
  fontawesome:

  # Internal version: 2.10.4
  # See: https://www.algolia.com
  # Example:
  # algolia_instant_js: //cdn.jsdelivr.net/npm/instantsearch.js@2/dist/instantsearch.js
  # algolia_instant_css: //cdn.jsdelivr.net/npm/instantsearch.js@2/dist/instantsearch.min.css
  algolia_instant_js:
  algolia_instant_css:

  # Internal version: 1.0.2
  # See: https://github.com/HubSpot/pace
  # Example:
  # pace: //cdn.jsdelivr.net/npm/pace-js@1/pace.min.js
  # pace: //cdnjs.cloudflare.com/ajax/libs/pace/1.0.2/pace.min.js
  # pace_css: //cdn.jsdelivr.net/npm/pace-js@1/themes/blue/pace-theme-minimal.css
  # pace_css: //cdnjs.cloudflare.com/ajax/libs/pace/1.0.2/themes/blue/pace-theme-minimal.min.css
  pace:
  pace_css:

  # Internal version: 1.0.0
  # See: https://github.com/theme-next/theme-next-canvas-nest
  # Example:
  # canvas_nest: //cdn.jsdelivr.net/gh/theme-next/theme-next-canvas-nest@1/canvas-nest.min.js
  # canvas_nest_nomobile: //cdn.jsdelivr.net/gh/theme-next/theme-next-canvas-nest@1/canvas-nest-nomobile.min.js
  canvas_nest: //cdn.jsdelivr.net/gh/theme-next/theme-next-canvas-nest@1.0.0/canvas-nest.min.js
  canvas_nest_nomobile: //cdn.jsdelivr.net/gh/theme-next/theme-next-canvas-nest@1.0.0/canvas-nest-nomobile.min.js

  # Internal version: 1.0.0
  # See: https://github.com/theme-next/theme-next-three
  # Example:
  # three: //cdn.jsdelivr.net/gh/theme-next/theme-next-three@1/three.min.js
  # three_waves: //cdn.jsdelivr.net/gh/theme-next/theme-next-three@1/three-waves.min.js
  # canvas_lines: //cdn.jsdelivr.net/gh/theme-next/theme-next-three@1/canvas_lines.min.js
  # canvas_sphere: //cdn.jsdelivr.net/gh/theme-next/theme-next-three@1/canvas_sphere.min.js
  three:
  three_waves:
  canvas_lines:
  canvas_sphere:

  # Internal version: 1.0.0
  # See: https://github.com/zproo/canvas-ribbon
  # Example:
  # canvas_ribbon: //cdn.jsdelivr.net/gh/theme-next/theme-next-canvas-ribbon@1/canvas-ribbon.js
  canvas_ribbon:

  # Internal version: 3.3.0
  # See: https://github.com/ethantw/Han
  # Example:
  # han: //cdn.jsdelivr.net/npm/han-css@3/dist/han.min.css
  # han: //cdnjs.cloudflare.com/ajax/libs/Han/3.3.0/han.min.css
  han:

  # Internal version: 4.0.7
  # See: https://github.com/vinta/pangu.js
  # Example:
  # pangu: //cdn.jsdelivr.net/npm/pangu@4/dist/browser/pangu.min.js
  # pangu: //cdnjs.cloudflare.com/ajax/libs/pangu/4.0.7/pangu.min.js
  pangu:

  # Internal version: 1.0.0
  # See: https://github.com/GoogleChromeLabs/quicklink
  # Example:
  # quicklink: //cdn.jsdelivr.net/npm/quicklink@1/dist/quicklink.umd.js
  quicklink:

  # Internal version: 1.0.0
  # See: https://github.com/revir/need-more-share2
  # Example:
  # needmoreshare2_js: //cdn.jsdelivr.net/gh/theme-next/theme-next-needmoreshare2@1/needsharebutton.min.js
  # needmoreshare2_css: //cdn.jsdelivr.net/gh/theme-next/theme-next-needmoreshare2@1/needsharebutton.min.css
  needmoreshare2_js:
  needmoreshare2_css:

  # Internal version: 1.0.0
  # See: https://github.com/theme-next/theme-next-bookmark
  # Example:
  # bookmark: //cdn.jsdelivr.net/gh/theme-next/theme-next-bookmark@1/bookmark.min.js
  bookmark:

  # Internal version: 1.1
  # See: https://github.com/theme-next/theme-next-reading-progress
  # Example:
  # reading_progress: //cdn.jsdelivr.net/gh/theme-next/theme-next-reading-progress@1/reading_progress.min.js
  reading_progress:

  # leancloud-storage
  # See: https://www.npmjs.com/package/leancloud-storage
  # Example:
  # leancloud: //cdn.jsdelivr.net/npm/leancloud-storage@3/dist/av-min.js
  leancloud:

  # valine
  # See: https://github.com/xCss/Valine
  # Example:
  # valine: //cdn.jsdelivr.net/npm/valine@1/dist/Valine.min.js
  # valine: //cdnjs.cloudflare.com/ajax/libs/valine/1.3.4/Valine.min.js
  valine:

  # gitalk & js-md5
  # See: https://github.com/gitalk/gitalk, https://github.com/emn178/js-md5
  # Example:
  # gitalk_js: //cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.min.js
  # gitalk_css: //cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.css
  # md5: //cdn.jsdelivr.net/npm/js-md5@0/src/md5.min.js
  gitalk_js:
  gitalk_css:
  md5:

  # likely
  # See: https://github.com/ilyabirman/Likely
  # Example:
  # likely_js: //cdn.jsdelivr.net/npm/ilyabirman-likely@2/release/likely.js
  # likely_css: //cdn.jsdelivr.net/npm/ilyabirman-likely@2/release/likely.css
  likely_js:
  likely_css:

  # DisqusJS
  # See: https://github.com/SukkaW/DisqusJS
  # Example:
  # disqusjs_js: //cdn.jsdelivr.net/npm/disqusjs@1/dist/disqus.js
  # disqusjs_css: //cdn.jsdelivr.net/npm/disqusjs@1/dist/disqusjs.css
  disqusjs_js:
  disqusjs_css:
# Assets
css: css
js: js
images: images
```

这里对部分配置进行描述，源文件中对每个配置也都有相应注释，这里就不一一细说。

作者：starsray

出处：<https://www.cnblogs.com/starsray/p/12058361.html>

版权：本作品采用「[署](https://www.cnblogs.com/starsray/p/名)」许可协议进行许可。

须知少日拏云志，曾许人间第一流

​ 分类: [Other](https://www.cnblogs.com/starsray/category/1846057.html)

​ 标签: [Hexo](https://www.cnblogs.com/starsray/tag/Hexo/)

Buy me a cup of coffee ☕.

-

-

​ [«](https://www.cnblogs.com/starsray/p/12058345.html) 上一篇： [Maven 添加 Tomcat 插件实现热部署](https://www.cnblogs.com/starsray/p/12058345.html)
​ [»](https://www.cnblogs.com/starsray/p/12067904.html) 下一篇： [使用 JMX 连接 JVM](https://www.cnblogs.com/starsray/p/12067904.html)

posted @ 2019-12-18 10:16 [starsray](https://www.cnblogs.com/starsray/) 阅读(1316) 评论(0) [编辑](https://i.cnblogs.com/EditPosts.aspx?postid=12058361) [收藏](<javascript:void(0)>) [举报](<javascript:void(0)>)
