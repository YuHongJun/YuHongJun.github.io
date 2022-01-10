---
author: Demi_YuHongJun
comments: true
date: 2021-01-01 06:42:32+00:00
layout: post
title: Linux 命令spawn-expect用法小记
description: Linux 命令spawn-expect用法小记
keywords: Linux
categories:
- Tech
- Linux
tags:
- Linux
---
* 目录
{:toc}
---


有时候我们使用命令行进行交互时，不想频繁的做一些重复的事情，例如：每次ssh远程登录时都需要输入密码。使用spawn和expect可以自动完成一些交互。

使用expect实现自动登录的脚本，网上有很多，可是都没有一个明白的说明，初学者一般都是照抄、收藏。可是为什么要这么写却不知其然。本文用一个最短的例子说明脚本的原理。

脚本代码如下：
#iterm2login.sh
```
#!/usr/bin/expect -f
set user xxx
set port 22
set host xxx
set password xxx
set timeout -1

spawn ssh $user@$host
expect {
        "(yes/no)" { send "yes\r"; exp_continue }
        "password:" { send "$password\r" }
}

#expect $login_name@*   {send "ls\r" }
interact
```

1. ［#!/usr/bin/expect］

这一行告诉操作系统脚本里的代码使用那一个shell来执行。这里的expect其实和linux下的bash、windows下的cmd是一类东西。

注意：这一行需要在脚本的第一行。

2. ［set timeout 30］

基本上认识英文的都知道这是设置超时时间的，现在你只要记住他的计时单位是：秒

3. ［spawn ssh -l username 192.168.1.1］

spawn是进入expect环境后才可以执行的expect内部命令，如果没有装expect或者直接在默认的SHELL下执行是找不到spawn命令的。所以不要用 “which spawn“之类的命令去找spawn命令。好比windows里的dir就是一个内部命令，这个命令由shell自带，你无法找到一个dir.com 或 dir.exe 的可执行文件。

它主要的功能是给ssh运行进程加个壳，用来传递交互指令。

4. ［expect "password:"］

这里的expect也是expect的一个内部命令，有点晕吧，expect的shell命令和内部命令是一样的，但不是一个功能，习惯就好了。这个命令的意思是判断上次输出结果里是否包含“password:”的字符串，如果有则立即返回，否则就等待一段时间后返回，这里等待时长就是前面设置的30秒

5. ［send "ispass\r"］

这里就是执行交互动作，与手工输入密码的动作等效。

温馨提示： 命令字符串结尾别忘记加上“\r”，如果出现异常等待的状态可以核查一下。

6. ［interact］

执行完成后保持交互状态，把控制权交给控制台，这个时候就可以手工操作了。如果没有这一句登录完成后会退出，而不是留在远程终端上。如果你只是登录过去执行

#!/usr/bin/expect #注意安装的路径，不确定 whereis expect 一下
![示例](https://yuhongjun.github.io/assets/media/01-2022/expect.png)
