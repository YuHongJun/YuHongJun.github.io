---
author: Demi_YuHongJun
comments: true
date: 2021-01-02 06:42:32+00:00
layout: post
title: Mac iterm2 安装配置rz、 sz命令
description: Mac iterm2 安装配置rz、 sz命令
keywords: Linux
categories:
- Mac
- iterm2
tags:
- iterm2
---
* 目录
{:toc}
---

在换了MacBook以后没有用到去如何链接远程服务器上传文件，最近闲下来的时候买了一个阿里服务器练手，突然想到不知道如何上传文件到远程阿里服务器，就去研究看了一下...

1、首先安装一下iterm2,Mac的客户端官方下载地址：https://www.iterm2.com/downloads.html

2、在本地下载lrzsz：

      brew install lrzsz

3、然后下载iterm2-send-zmodem和iterm2-recv-zmodem，把文件保存到/usr/local/bin/ 路径下

    下载地址：https://github.com/YuHongJun/rzsz
    
4、添加权限

      cd /usr/local/bin

      chmod +x iterm2-send-zmodem.sh

      chmod +x iterm2-recv-zmodem.sh

5、设置iterm2的触发器（triggers）
    执行如下以下步骤：command+“,” 组合键打开item2的“Preferences”面板->Profiles选项卡->Advanced->Triggers（点击Edit即可）

     Regular expression: \*\*B0100
     Action: Run Silent Coprocess
     Parameters: /usr/local/bin/iterm2-send-zmodem.sh


    Regular expression: \*\*B00000000000000
    Action: Run Silent Coprocess
    Parameters: /usr/local/bin/iterm2-recv-zmodem.sh    
    

![示例](https://yuhongjun.github.io/assets/media/01-2022/iterm2-trigger.png)

如果使用iterm2远程ssh连接服务器，服务器端需要安装lrzsz包。