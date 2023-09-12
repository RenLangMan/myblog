---
title: "Let'sEncrypt 免费通配符/泛域名SSL证书添加使用教程"
description: 'LetsEncrypt免费通配符泛域名SSL证书添加使用教程'
keywords: 'LetsEncrypt免费通配符泛域名SSL证书添加使用教程'

date: 2022-10-25T14:22:00+08:00
lastmod: 2023-09-12T12:00:19+08:00

categories:
  - ssl
tags:
  - 泛域名SSL证书
  -
author: 任浪漫
abbrlink: 503438718
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
#url: "letsencrypt免费通配符泛域名ssl证书添加使用教程.html"
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

## [Let'sEncrypt 免费通配符/泛域名 SSL 证书添加使用教程](https://lnmp.org/faq/letsencrypt-wildcard-ssl.html)

​ 作者：licess 发布时间：2018 年 03 月 14 日 分类：[常见问题](https://lnmp.org/category/faq/)

[![letsencrypt.png](https://lnmp.org/usr/uploads/2018/03/1266700038.png)![lnmp一键安装包](https://lnmp.org/images/logo.gif)](https://lnmp.org/)
Wildcard certificate 俗称野卡正式点一般称为通配符或泛域名证书，也就是为\*.lnmp.org 签发包含所有子域名的 SSL 证书，从去年 6、7 月份左右就已经说过 Let'sEncrypt 将于 2018 年 1 月支持，但是几次放鸽子后最近终于证书支持了。通配符证书一般还是比较贵的一般最便宜的通配符证书 5、60 美元一年，只不过 Let'sEncrypt 的有效期是 3 个月，对于一般用户来说基本没差别。

LNMP 1.5 或更高版本已经添加了对通配符证书的支持，生成通配符证书和 Let'sEncrypt 平常 SSL 证书命令有些差异（通配符证书命令是 **lnmp dnsssl** 域名 dns 服务商简称，普通证书是**lnmp ssl add**），最好是使用域名 DNS 服务商的 API，这样才能实现自动续期。

<!-- more -->

## 域名 DNS 服务商 API 方式生成 SSL 证书

**如果要生成通配符证书，首先要准备好一下东西：**

-

- 域名一枚

- 支持该域名 DNS 服务商并在后面表格找到名称及简称

- 域名 DNS 服务商 API 操作所需的参数，如 Key、Secret 或 Token 之类的。

- 已安装 lnmp 1.8 或者升级到 1.8 及更高版本(不确定的话可以下载最新的安装包，安装包目录下运行 ./upgrade1.x-1.8.sh))

-

- - 下面我们以

  - 阿里云 DNS

  - 为例，需要到

  - https://ram.console.aliyun.com/users

  - 这里创建子账户，选择"Open API 调用访问"，获取 API KEY 和 SECRET KEY（文章最后我们会附上常见域名 DNS 服务商的简称、获取 API 方法和所需的参数）。

  - 通过表格可以知道，

  - 阿里云 DNS

  - 的简称为 ali，我们前面获取到了 API KEY 和 SECRTET KEY，需要先在在终端里将 API 操作所需的参数输出供程序使用，命令如下：

  -

  - > **export Ali_Key="123456"** > **export Ali_Secret="abcdef"**

  - 注意！注意！注意！这里只是例子，其他域名 DNS 服务的 API 参数命令可以在文章后面对照表中查找，别照抄！别照抄！别照抄！，该项必须 export，否则将提示 You don't specify dnspod api key and key id yet.失败，而且是严格区分大小写！！！

    下面开工开始添加虚拟主机并生成通配符 SSL 证书，命令：**lnmp dnsssl ali** 或 **lnmp dns ali** 注意！注意！注意！ali 为 DNS 服务商的简称，下面对照表中查找，别照抄！别照抄！别照抄！如 dnspod 的 DNS 就把 ali 就改成 dp ！！！

    **ali 为域名 DNS 服务商的简称，如果使用的其他 DNS 服务商更换为其他 DNS 服务商的简称，可以在文章后面对照表格里查看 DNS 服务商对应简称。**

    ![lnmp-1.5-dnsssl.png](https://lnmp.org/usr/uploads/2018/03/1051585099.png)
    分别按提示输入域名、添加更多域名（多个域名空格隔开，如 _.lnmp.org _.test.lnmp.org）、网站目录、是否启用日志等选项，详细介绍可以看上图文字注释。

    **注意：如果要生成通配符/泛域名 SSL 证书，输入其他域名时不要输入www.lnmp.org 的域名，否则将生成失败！！！**

    如果之前输出的 API 参数没问题的话，等几分钟就会生成完毕，并提示"Let's Encrypt SSL Certificate create successfully."。

    再 https://www.你的域名.com 访问就可以了。

  - ## 使用域名 DNS 服务商 API 方式只生成 SSL 证书不创建网站配置文件

  - 该方式只在 lnmp 1.6 或更高版本上有，其他版本的可以升级到 1.6 进行使用。
    命令：**lnmp onlyssl ali 注意！注意！注意！ali 为 DNS 服务商的简称，下面对照表中查找，别照抄！别照抄！别照抄！如 dnspod 的 DNS 就 ali 就改成 dp ！！！**
    这里的 ali 和上述带配置文件的参数是一样的，如果是其他 DNS 服务商，参考下面表格进行更改。只不过在添加过程中不需要输入网站目录、是否开启日志等选项。
    该模式下之创建 SSL 证书并不生成网站配置文件，方便用户在多个虚拟主机上使用同一个证书。自己可以另外 lnmp vhost add 或 lnmp ssl add 创建 SSL 站点配置文件

    **域名 DNS 服务商名称、简称、API 参数和开通 API 对照表**
    API 参数中 Key、Secret 等之类的参数都要改成你自己 API 的不然一样不行

  - | 服务商名称                                            | 服务商简称 | 所需 API 参数                                                                      | 获取 API 参数地址                                                                |
    | ----------------------------------------------------- | ---------- | ---------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
    |                                                       |            |                                                                                    |                                                                                  |
    | dnspod (cn 大陆版)                                    | dp         | export DP_Id="123456" export DP_Key="abcdef"                                       | [点击访问](https://www.dnspod.cn/console/user/security)                          |
    | [aliyun](https://www.vpser.net/go/aliyun)             | ali        | export Ali_Key="123456" export Ali_Secret="abcdef"                                 | [点击访问](https://ram.console.aliyun.com/users)                                 |
    | cloudflare                                            | cf         | export CF_Key="123456" export CF_Email="[abc@example.com](mailto:abc@example.com)" | [点击访问](https://dash.cloudflare.com/profile/api-tokens)                       |
    | [linode](https://www.vpser.net/go/linode)             | linode     | export LINODE_API_KEY="123456"                                                     | [点击访问](https://manager.linode.com/profile/api)                               |
    | he                                                    | he         | export HE_Username="username" export HE_Password="password"                        | [he](https://dns.he.net)的用户名密码                                             |
    | [digitalocean](https://www.vpser.net/go/digitalocean) | dgon       | export DO_API_KEY="123456"                                                         | [点击访问](https://cloud.digitalocean.com/settings/applications)                 |
    | [namesilo](https://www.vpser.net/go/namesilo)         | namesilo   | export Namesilo_Key="123456"                                                       | [点击访问](https://www.namesilo.com/account_api.php)                             |
    | aws                                                   | aws        | export AWS_ACCESS_KEY_ID=123456 export AWS_SECRET_ACCESS_KEY=abcdef                | [点击访问](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html) |
    | [namecom](https://www.vpser.net/go/name)              | namecom    | export Namecom_Username="username" export Namecom_Token="123456"                   | [点击访问](https://www.name.com/reseller/apply)                                  |
    | freedns                                               | freedns    | export FREEDNS_User="username" export FREEDNS_Password="password"                  | [freedns](https://freedns.afraid.org)的用户名密码                                |
    | godaddy                                               | gd         | export GD_Key="123456" export GD_Secret="abcdef"                                   | [点击访问](https://developer.godaddy.com/keys/)                                  |
    | yandex                                                | yandex     | export PDD_Token="abcdef"                                                          | [点击访问](https://tech.yandex.com/domain/doc/concepts/access-docpage/)          |

  - 这里只列出了国内用户使用比较多的 DNS 服务商，也可以去 https://github.com/Neilpang/acme.sh/tree/master/dnsapi 查看其他服务商的具体使用方法。

  - ## 手动 DNS 添加 TXT 记录生成 SSL

  - 当然还有另外一种方式也是采用 DNS，但是需要手动在域名 DNS 服务商那边添加 TXT 记录，命令是：**lnmp dnsssl** 或 **lnmp dns**
    注意使用手动 DNS 将无法自动续期！！！

    添加虚拟主机过程的信息和前面使用 API 所填写的信息都是一样的，只不过不需要 export API 的相关信息。

    ![lnmp-1.5-dns-manual-add-records.png](https://lnmp.org/usr/uploads/2018/03/2750901719.png)
    出现改提示就需要去域名 DNS 服务商网站上手动添加上提示的主机记录和值，如果是添加的二级域名，如图，就需要在域名 DNS 服务商后台上添加的 TXT 主机记录为\_acme-challenge.vpser

    值为图中黄色框中的绿色的所有字符。如果是为 lnmp.org 生成 SSL 证书的话主机记录直接添加 \_acme-challenge 就可以了，注意如果添加多个域名每个域名都要按提示的主机记录和值添加到域名 DNS 服务商后台上。

    ![lnmp-1.5-cloudxns-records.png](https://lnmp.org/usr/uploads/2018/03/2702555284.png)

    如果添加的主机记录和记录值都没问题的话就会自动生成证书并添加好虚拟主机，就可以直接使用了。

  - ## HTTPS 绿锁问题的说明

  - 常说的绿锁即![img](https://www.vpser.net/uploads/2018/03/ssl-padlock.png)在域名前面有一把绿锁的锁，表示该网站在使用 https 安全协议链接的。

    ![website-secure-info-not.png](https://lnmp.org/usr/uploads/2018/03/3224338824.png)
    状态的话就这 3 中，安全的、信息或不安全和不安全或危险。

  - ### 最常见不显示绿锁的原因

  - 该页面上有 http 不安全的资源加载，如图片、js、css 之类的，最简单的排查方法 Chrome 中按 F12、点击 Console 选项卡再 F5 刷新页面，就会有 Mixed Content: The page at 'https://lnmp.org/install.html' was loaded over HTTPS, but requested an insecure image 'http://lnmp.org/images/1.4/lnmp1.4-install-1.png'. This content should also be served over HTTPS. 之类的提示，就是说明了在 install.html 这个页面上有 lnmp1.4-install-1.png 这个文件的是使用 http 加载的。找到对应的地方改成 https 链接就可以了。

    如果证书到期或者域名与改 SSL 证书里的域名不匹配的话就会显示不安全或危险。

    如在使用过程中有任何问题可以在[论坛反馈](https://bbs.vpser.net/forum-25-1.html)。

  - 标签: [let'sencrypt](https://lnmp.org/tag/let-sencrypt/), [免费 ssl 证书](https://lnmp.org/tag/免费ssl证书/), [免费通配符 ssl 证书](https://lnmp.org/tag/免费通配符ssl证书/), [泛域名证书](https://lnmp.org/tag/泛域名证书/), [免费野卡证书](https://lnmp.org/tag/免费野卡证书/), [ssl 证书教程](https://lnmp.org/tag/ssl证书教程/), [泛域名 ssl 证书](https://lnmp.org/tag/泛域名ssl证书/)
