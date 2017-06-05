---
author: Demi_YuHongJun
comments: true
date: 2017-06-05 09:42:32+00:00
layout: post
title: Finders Keepers(中级 算法)
description: Finders Keepers(中级 算法)
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---

https://www.freecodecamp.cn/challenges/finders-keepers

写一个 function，它浏览数组（第一个参数）并返回数组中第一个通过某种方法（第二个参数）验证的元素。

如果你被卡住了，记得开大招 Read-Search-Ask。尝试与他人结伴编程、编写你自己的代码。

这是一些对你有帮助的资源:

[Array.filter()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

解法：
```javascript
function find(arr, func) {
  var num = 0;
  var length=arr.filter(func).length;
  if(length>0){
    num=arr.filter(func)[0];
  }else{
    num=undefined;
  }
  return num;
}

find([1, 3, 5, 9], function(num){ return num % 2 === 0; });

```
