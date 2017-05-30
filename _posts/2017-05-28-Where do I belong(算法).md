---
author: Demi_YuHongJun
comments: true
date: 2017-05-28 10:42:32+00:00
layout: post
title: Where do I belong (算法)
description: Where do I belong (算法)
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---
https://www.freecodecamp.cn/challenges/where-do-i-belong

我身在何处？

先给数组排序，然后找到指定的值在数组的位置，最后返回位置对应的索引。

举例：where([1,2,3,4], 1.5) 应该返回 1。因为1.5插入到数组[1,2,3,4]后变成[1,1.5,2,3,4]，而1.5对应的索引值就是1。

同理，where([20,3,5], 19) 应该返回 2。因为数组会先排序为 [3,5,20]，19插入到数组[3,5,20]后变成[3,5,19,20]，而19对应的索引值就是2。

当你完成不了挑战的时候，记得开大招'Read-Search-Ask'。

这是一些对你有帮助的资源:

[Array.sort()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

解法
```
function where(arr, num) {
  // Find my place in this sorted array.
  arr.push(num);
var result=arr.sort((a,b)=>{return a-b});  
  return result.indexOf(num);
}

where([40, 60], 50);


```