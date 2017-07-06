---
author: Demi_YuHongJun
comments: true
date: 2017-06-14 04:42:32+00:00
layout: post
title: 2017-06-14
description: 2017-06-14
keywords: Error: watch ENOSPC
categories:
- Tech
tags:
- Error: watch ENOSPC
---
* 目录
{:toc}
---

Fedora&Ubuntu 下使用gulp 报错 Error: watch ENOSPC 解决方案

用gulp启动,错误如下

```
Error: watch ENOSPC
 at exports._errnoException (util.js:746:11)
 at FSWatcher.start (fs.js:1172:11)
 at Object.fs.watch (fs.js:1198:11)
```
解决方案：

当前问题主要是因为gulp的watch需要监听很多文件的改动,但是fedora、ubuntu系统的文件句柄其实是有限制的,因此可以使用以下命令：

```echo fs.inotify.max_user_watches=524288 | sudo tee -a /etc/sysctl.conf && sudo sysctl -p```

亲测可以使用，如果对你有用的话，麻烦推荐下，共勉之，谢谢。