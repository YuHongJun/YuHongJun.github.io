---
author: Demi_YuHongJun
comments: true
date: 2017-05-30 09:42:32+00:00
layout: post
title: Sum All Numbers in a Range(算法 中级)
description: Sum All Numbers in a Range(算法 中级)
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---

https://www.freecodecamp.cn/challenges/sum-all-numbers-in-a-range

我们会传递给你一个包含两个数字的数组。返回这两个数字和它们之间所有数字的和。

最小的数字并非总在最前面。

如果你被难住了，记得使用 Read-Search-Ask。尝试与他人结伴编程、编写你自己的代码。

这是一些对你有帮助的资源:

[Math.max()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/max)

[Math.min()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/min)

[Array.reduce()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)

解法一:

```javascript
function sumAll(arr) {
 var array=[], sum;
   var max=Math.max.apply(null,arr);
   var min=Math.min.apply(null,arr);
   var sumFun=function(max,min){
      for(var i=0;i<(max-min+1);i++){
         array.push(min+i);
      }
      array.reduce(function(previousValue,currentValue){
         return previousValue+currentValue;
      });
   };
   sum=sumFun(max,min);
   return sum;
}
sumAll([1, 4]);
```
解法二:(推荐)
```javascript
function sumAll(arr) {
  return (arr[0] + arr[1])*(Math.abs(arr[0] - arr[1]) + 1)/2;
}

sumAll([1, 4]);
```
解法三:
```javascript
function sumAll(arr) {
  var result=0,
  a_start=Math.min(arr[0],arr[1]),
  a_end=Math.max(arr[0],arr[1]);
  while(a_start<=a_end){
    result+=a_start;
    a_start++;
  }
  return result;
}

sumAll([1, 4]);
```