---
author: Demi_YuHongJun
comments: true
date: 2021-01-10 06:42:32+00:00
layout: post
title: docker Redis容器通过dump.rdb文件进行数据迁移或恢复数据
description: docker Redis容器通过dump.rdb文件进行数据迁移或恢复数据
keywords: Linux
categories:
- Redis
- Docker
tags:
- Redis
---
* 目录
{:toc}
---

在换了MacBook以后没有用到去如何链接远程服务器上传文件，最近闲下来的时候买了一个阿里服务器练手，突然想到不知道如何上传文件到远程阿里服务器，就去研究看了一下...

1、拉取Redis镜像
```
# 拉取最新的Redis镜像
$docker pull redis
```
2、进入旧的Redis容器保存数据
```
$docker exec -it old_docker_redis redis-cli
127.0.0.1:6379>save
```
3、拷贝dump.rdb文件

通过上一步save命令会生成dump.rdb文件，如果不知道生成的文件保存在什么位置可以通过 docker inspect 容器名 查看容器信息在MOUNTS 下的Source的值可以看到保存位置
```
$ docker run -it --name new_docker_redis -v /home/yhj/data/dump.rdb:/data/dump.rdb -p 6379:6379 redis:latest /bin/bash
$ redis-server
```
    
4、直接拉取的Redis镜像没有配置文件，需要自己下载配置文件，配置文件下载地址：https://download.redis.io/releases/ 。
比如我的版本是5.0.3 将修改后的配置文件挂载到容器里。然后启动Redis服务时指定配置文件即可。

```
$ $ docker run -it --name new_docker_redis -v /home/yhj/data/redis.conf:/data/redis.conf -p 6379:6379 redis:latest /bin/bash
$ redis-server /data/redis.conf
```
