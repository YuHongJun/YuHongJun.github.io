---
author: Demi_YuHongJun
comments: true
date: 2015-05-25 07:43:08+00:00
layout: post
title: Mac nodejs npm 安装-global包 权限修复
categories:
- Tech
tags:
- javascript
- nodejs
- npm
---

最近换成在mac上面玩NodeJs和npm，结果遇到了权限问题。顺利安装玩node和npm之后用npm 的-global一直安装不上package。
 
```  
npm ERR!   errno: 3,
npm ERR!   code: 'EACCES'
```   

首先可以通过在系统下重构一下npm，通过从最新的git抓取来make install

```   
git clone http://github.com/isaacs/npm.git
cd npm
sudo make install
```   

之后进行-global的权限修改。
    
```   
sudo chown -R $USER /usr/local
//use for local user
```    

或者用另一种更适合于-global安装的修改方式。

```
sudo chown -R `whoami` ~/.npm
//better for -global install
```   

这样之后你再试试跑nodeschool上面的教程试试看，应该已经可行了。
