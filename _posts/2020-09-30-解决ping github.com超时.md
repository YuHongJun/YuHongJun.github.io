---
author: Demi_YuHongJun
comments: true
date: 2020-09-30 05:42:32+00:00
layout: post
title: ping github.com timeout
description: 解决ping github.com超时
keywords: Deploy
categories:
- Tech
tags:
- Git
---
* 目录
{:toc}
---

### 解决ping github.com超时 解决Github打不开问题

```
kex_exchange_identification: connection closed by remote host fatal: could not read from remote repository
```
我在做项目开发的时候突然遇到git命令失败，猜想可能是连不上github.com。
于是我用命令ping了一下github.com，发现果然全部超时。

那么现在来解决一下这个问题：
首先打开[DNS查询工具](https://tools.ipip.net/dns.php),
[IPAddress](https://github.com.ipaddress.com/)，
输入 github.com, github.global.ssl.fastly.net, assets-cdn.github.com 查询。
选取解析响应时间最短的DNS-IP，然后复制到private/etc/hosts里面。

以下是macos上使用命令行打开方式，也可以直接在硬盘上找到这个文件打开
```
sudo vim /private/etc/hosts
```
然后将地址拷贝进来，后面再加上github.com
```
   199.232.69i.194 github.global.ssl.fastly.net
   140.82.113.4 github.com
   205.251.197.3 github.com
   185.199.108.153 assets-cdn.github.com
   185.199.110.153 assets-cdn.github.com
   185.199.111.153 assets-cdn.github.com
   185.199.108.133 avatars0.githubusercontent.com
   185.199.109.133 avatars0.githubusercontent.com
   185.199.108.133 avatars1.githubusercontent.com
```
cmd:ipconfig /flushdns
再次ping github.com发现ping通了

![示例](https://yuhongjun.github.io/assets/media/09-2020/2020-09-30.png)