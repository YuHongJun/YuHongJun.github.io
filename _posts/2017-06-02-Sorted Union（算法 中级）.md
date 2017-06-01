---
author: Demi_YuHongJun
comments: true
date: 2017-06-02 09:42:32+00:00
layout: post
title: Sorted Union（算法 中级）
description: Sorted Union（算法 中级）
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---
https://www.freecodecamp.cn/challenges/sorted-union

写一个 function，传入两个或两个以上的数组，返回一个以给定的原始数组排序的不包含重复值的新数组。

换句话说，所有数组中的所有值都应该以原始顺序被包含在内，但是在最终的数组中不包含重复值。

非重复的数字应该以它们原始的顺序排序，但最终的数组不应该以数字顺序排序。

请参照下面验证判断中的例子。

如果你被卡住了，记得开大招 Read-Search-Ask。尝试与他人结伴编程、编写你自己的代码。

这是一些对你有帮助的资源:

[Arguments object](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/arguments)

[Array.reduce()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)

思路

主干思路很清晰，先拼接数组，再去重。

先把所有参数拼接成数组，这需要用到 Array 的归并方法 reduce() 。但传进来的参数 arguments 只是类数组对象，我们首先要把它转化为真正的数组：

var args = Array.from(arguments);
然后得到一个拼接而成的大数组：

var arr=args.reduce(function(accumulator, currentValue, currentIndex, array){
  return accumulator.concat(currentValue);
  });
最后用`filter()`方法去重：

var result=arr.filter(function(item,index,array){
  return array.indexOf(item)===index;
});

解法一：
```javascript
function unite(arr1, arr2, arr3) {
  var args = Array.from(arguments);
  var arr=args.reduce(function(accumulator, currentValue, currentIndex, array){
  return accumulator.concat(currentValue);
  });
var result=arr.filter(function(item,index,array){
  return array.indexOf(item)===index;
});
  
  return result;
}

unite([1, 3, 2], [5, 2, 1, 4], [2, 1]);

```

解法二：
```javascript
function unite(arr1, arr2, arr3) {
   if(arguments.length === 1){
    return arguments[0];
  }
  var arr = [],
      res = [];
  for(var i=0,len=arguments.length;i<len;i++){
    arr = arguments[i];
    for(var j=0;j<arr.length;j++){
      //如果结果数组中不存在该值则放入数组
      if(res.indexOf(arr[j]) === -1){
        res.push(arr[j]);
      }
    }
  }
  return res;
}

unite([1, 3, 2], [5, 2, 1, 4], [2, 1]);

```