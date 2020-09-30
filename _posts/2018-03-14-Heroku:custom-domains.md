---
author: Demi_YuHongJun
comments: true
date: 2018-03-14 05:42:32+00:00
layout: post
title: Custom Domain Names for Apps
description: Custom Domain Names for Apps
keywords: Deploy
categories:
- Tech
tags:
- Heroku
---
* 目录
{:toc}
---

https://devcenter.heroku.com/articles/custom-domains

Heroku 會提供一個預設的域名，即[name of app].herokuapp.com，如果你不喜歡可以繫結自己的域名。 繫結 繫結方式比較簡單，直接修改 DNS 指向到 Heroku，然後配置Heroku 即可。
修改 DNS 在 Heroku 專案目錄使用 heroku domains 命令檢視當前專案的域名，為 DNS 新增 CNAME 指向到該域名。
配置 Heroku 使用 heroku domains:add 命令新增域名到 Heroku，然後等待即可。
