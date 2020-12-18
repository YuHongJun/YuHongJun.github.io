---
author: Demi_YuHongJun
comments: true
date: 2020-09-30 05:42:32+00:00
layout: post
title: Github
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

### 解决ping github.com超时

```
kex_exchange_identification: connection closed by remote host fatal: could not read from remote repository
```
我在做项目开发的时候突然遇到git命令失败，猜想可能是连不上github.com。
于是我用命令ping了一下github.com，发现果然全部超时。

那么现在来解决一下这个问题：
首先打开[DNS查询工具](https://tools.ipip.net/dns.php) [IPAddress](https://github.com.ipaddress.com/)，输入github.com然后点击查询。
选取解析响应时间最短的DNS-IP，然后复制到private/etc/hosts里面。

以下是macos上使用命令行打开方式，也可以直接在硬盘上找到这个文件打开
```
sudo vim /private/etc/hosts
```
然后将地址拷贝进来，后面再加上github.com
```
140.82.112.4 github.com
211.167.242.34  github.com
```
再次ping github.com发现ping通了

![示例](https://yuhongjun.github.io/assets/media/2020-09-30.png)