---
author: Demi_YuHongJun
comments: true
date: 2017-05-28 09:42:32+00:00
layout: post
title: Seek and Destroy(算法)
description: Seek and Destroy(算法)
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---
https://www.freecodecamp.cn/challenges/seek-and-destroy

金克斯的迫击炮！

实现一个摧毁(destroyer)函数，第一个参数是待摧毁的数组，其余的参数是待摧毁的值。

当你完成不了挑战的时候，记得开大招'Read-Search-Ask'。

这是一些对你有帮助的资源:

[Arguments object](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/arguments)

[Array.filter()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

解法
```
function destroyer(arr) {
  // Remove all the values
   var argsBeRemove = [...arguments];
   argsBeRemove.shift();
 var result= arr.filter((val)=>{
    return  argsBeRemove.indexOf(val)==-1;
  });
  return  result;
}

destroyer([1, 2, 3, 1, 2, 3], 2, 3);

```
