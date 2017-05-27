---
author: Demi_YuHongJun
comments: true
date: 2017-05-27 10:42:32+00:00
layout: post
title: Falsy Bouncer(算法)
description: Falsy Bouncer(算法)
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---

https://www.freecodecamp.cn/challenges/falsy-bouncer

真假美猴王！

删除数组中的所有假值。

在JavaScript中，假值有false、null、0、""、undefined 和 NaN。

当你完成不了挑战的时候，记得开大招'Read-Search-Ask'。

这是一些对你有帮助的资源:

[Boolean Objects](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Boolean)
[Array.filter()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

解法

```javascript
function bouncer(arr) {
  // Don't show a false ID to this bouncer. 
 var result= arr.filter(Boolean);
  return result;
}

bouncer([7, "ate", "", false, 9]);

```