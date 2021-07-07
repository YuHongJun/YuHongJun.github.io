---
author: Demi_YuHongJun
comments: true
date: 2021-06-09 05:42:32+00:00
layout: post
title: Mac SecureCRT 重置试用
description: Mac SecureCRT 重置试用
keywords: Deploy
categories:
- Tech
tags:
- windows
- mac
---
* 目录
{:toc}
---

## Mac SecureCRT 重置试用

Mac SecureCRT 重置试用

1. 下载安装
https://www.vandyke.com/download/securecrt/6.7/index.html

2. 试用到期后

```
cd /Users/xxx/Library/Application\ Support/VanDyke/SecureCRT/Config
rm SecureCRT_eval.lic
```
3. crontab 定时任务 每月28号4点45分 删除
vim reset_time_crontab
```
  # delete the securecrt lic for free 30days yhj
  45 4 28 * * rm $HOME/Library/Application\ Support/VanDyke/SecureCRT/Config/SecureCRT_eval.lic > $HOME/Library/Application\ Support/VanDyke/SecureCRT/Config    /reset_cron.log 2>&1
```
crontab reset_time_crontab
