---
author: Demi_YuHongJun
comments: true
date: 2021-01-10 06:42:32+00:00
layout: post
title: 前端进阶-从多线程到Event Loop全面梳理
description: 前端进阶-从多线程到Event Loop全面梳理
keywords: javascript
categories:
- frontend
- javascript
tags:
- javascript
---
* 目录
{:toc}
---

## 引子
几乎在每一本JS相关的书籍中，都会说JS是单线程的，JS是通过事件队列(Event Loop)的方式来实现异步回调的。
对很多初学JS的人来说，根本搞不清楚单线程的JS为什么拥有异步的能力，所以，我试图从进程、线程的角度来解释这个问题。

## CPU

计算机的核心是CPU，它承担了所有的计算任务。

它就像一座工厂，时刻在运行。

## 进程

假定工厂的电力有限，一次只能供给一个车间使用。
也就是说，一个车间开工的时候，其他车间都必须停工。
背后的含义就是，单个CPU一次只能运行一个任务。
进程就好比工厂的车间，它代表CPU所能处理的单个任务。
进程之间相互独立，任一时刻，CPU总是运行一个进程，其他进程处于非运行状态。
CPU使用时间片轮转进度算法来实现同时运行多个进程。

## 线程
一个车间里，可以有很多工人，共享车间所有的资源，他们协同完成一个任务。

线程就好比车间里的工人，一个进程可以包括多个线程，多个线程共享进程资源。

## CPU、进程、线程之间的关系
从上文我们已经简单了解了CPU、进程、线程，简单汇总一下。
```
进程是cpu资源分配的最小单位（是能拥有资源和独立运行的最小单位）
线程是cpu调度的最小单位（线程是建立在进程的基础上的一次程序运行单位，一个进程中可以有多个线程）
不同进程之间也可以通信，不过代价较大
单线程与多线程，都是指在一个进程内的单和多
```

## 浏览器是多进程的
我们已经知道了CPU、进程、线程之间的关系，对于计算机来说，每一个应用程序都是一个进程，
而每一个应用程序都会分别有很多的功能模块，这些功能模块实际上是通过子进程来实现的。

对于这种子进程的扩展方式，我们可以称这个应用程序是多进程的。
而对于浏览器来说，浏览器就是多进程的，我在Chrome浏览器中打开了多个tab，然后打开windows控制管理器：
