---
author: Demi_YuHongJun
comments: true
date: 2015-05-31 05:03:36+00:00
layout: post
title: Github设置，强制使用"https://" 来代替 "git://"
categories:
- Tech
tags:
- github
- npm
---

有时候你会遇到无法用"git://"去克隆一个[github](http://github.com)上面的repository。这是因为电脑的网络代理设置或者防火墙设置禁止了对 **"git://"** 的访问。这种时候只能用**https://**来调用游览器端口来对repository进行访问。可以在Terminal里面输入以下指令：

   ```
   $ git config --global url."https://".insteadOf git://
   
   ```

这样之后你的**.gitconfig**里面就会多出以下设置：

   ```
   [url "https://"]   
       insteadOf = git://
   ```

这样设置完以后你就不用管你在Terminal里面进行克隆时，用的是**"git://"** 还是 **"https://"**。当你进行repo克隆时，两个种方式都会最终用**"https://"**来进行连接并正常的工作。
