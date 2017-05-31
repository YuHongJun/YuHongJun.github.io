---
author: Demi_YuHongJun
comments: true
date: 2017-05-31 09:42:32+00:00
layout: post
title: Diff Two Arrays(算法)
description: Diff Two Arrays(算法)
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---

https://www.freecodecamp.cn/challenges/diff-two-arrays

比较两个数组，然后返回一个新数组，该数组的元素为两个给定数组中所有独有的数组元素。换言之，返回两个数组的差异。

如果你被难住了，记得使用 Read-Search-Ask尝试与他人结伴编程、编写你自己的代码。

这是一些对你有帮助的资源:
[Comparison Operators](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Comparison_Operators)

[Array.slice()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)

[Array.filter()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

[Array.indexOf()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf)

[Array.concat()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/concat)

解法一（Arrow Function）
``` 
function diff(arr1, arr2) {
  var newArr = [];
  // Same, same; but different.
var arr1Diff = arr1.filter((cur) => {
    return arr2.indexOf(cur) === -1;
  });
  var arr2Diff = arr2.filter((cur) => {
    return arr1.indexOf(cur) === -1;
  });
  newArr = arr1Diff.concat(arr2Diff);
  return newArr;
}

diff([1, 2, 3, 5], [1, 2, 3, 4, 5]);

```
解法二
```javascript
function diff(arr1, arr2) {
   return arr1.filter(function(v){
   return arr2.indexOf(v)==-1;        //第一个数组在第二个数组中不同的项
  }).concat(arr2.filter(function(v){
   return arr1.indexOf(v)==-1;
  }));  
}

diff([1, 2, 3, 5], [1, 2, 3, 4, 5]);

```







