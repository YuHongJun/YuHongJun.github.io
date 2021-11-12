---
author: Demi_YuHongJun
comments: true
date: 2021-11-01 05:42:32+00:00
layout: post
title: pm2日志分割 pm2-logrotate
description: pm2日志分割 pm2-logrotate
keywords: pm2
categories:
- Tech
tags:
- pm2
- Mac
---
* 目录
{:toc}
---

## pm2日志分割 pm2-logrotate


安装pm2 install pm2-logrotate

安装成功后 通过pm2 list 可以查看

pm2默认会将日志存储在/root/.pm2/logs下。

通过项目中设置pm2启动配置 日志存储设置

设置格式

pm2 set pm2-logrotate:{paramName} {value}

命令设置具体的参数，支持的参数有：

l Compress：是否通过gzip压缩日志

l max_size：单个日志文件的大小，比如上图中设置为1K（这个其实太小了，实际文件大小并不会严格分为1K）

l retain：保留的日志文件个数，比如设置为10,那么在日志文件达到10个后会将最早的日志文件删除掉

l dateFormat：日志文件名中的日期格式，默认是YYYY-MM-DD_HH-mm-ss，注意是设置的日志名+这个格式，如设置的日志名为abc.log，那就会生成abc_YYYY-MM-DD_HH-mm-ss.log名字的日志文件

l rotateModule：把pm2本身的日志也进行分割  设置true不会对默认的日志分割，设置false会对默认日志进行分割（默认日志和新设置的日志只能生效一种）

l workerInterval：设置启动几个工作进程监控日志尺寸，最小为1

rotateInterval：设置强制分割，默认值是0 0 * * *，意思是每天晚上0点分割

0 0 * * *  对应 分钟 小时 日 月 周几（0-7），*表示通配符

16 * * * *  表示每小时第16分钟分割日志

0 16 * * * 表示每天16点0分分割日志

配置 例子

$ pm2 set pm2-logrotate:max_size 10M

$ pm2 set pm2-logrotate:retain 7

$ pm2 set pm2-logrotate:compress false

$ pm2 set pm2-logrotate:dateFormat YYYY-MM-DD_HH-mm-ss

$ pm2 set pm2-logrotate:workerInterval 30

$ pm2 set pm2-logrotate:rotateInterval 10 * * * *

$ pm2 set pm2-logrotate:rotateModule true

配置完成后要重启pm2

pm2 restart all

查看配置

pm2 conf pm2-logrotate