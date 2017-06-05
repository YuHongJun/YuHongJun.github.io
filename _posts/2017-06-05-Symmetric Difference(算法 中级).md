---
author: Demi_YuHongJun
comments: true
date: 2017-06-05 16:42:32+00:00
layout: post
title: Symmetric Difference(算法 中级)
description: Symmetric Difference(算法 中级)
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---

https://www.freecodecamp.cn/challenges/symmetric-difference

创建一个函数，接受两个或多个数组，返回所给数组的 `对等差分(symmetric difference)` (`△ or ⊕`)数组.

给出两个集合 (如集合 `A = {1, 2, 3`} 和集合 `B = {2, 3, 4}`), 而数学术语 "对等差分" 的集合就是指由所有只在两个集合其中之一的元素组成的集合(`A △ B = C = {1, 4}`). 对于传入的额外集合 (如 `D = {2, 3}`), 你应该安装前面原则求前两个集合的结果与新集合的对等差分集合 (`C △ D = {1, 4} △ {2, 3} = {1, 2, 3, 4}`).

当你遇到困难的时候，记得查看错误提示、阅读文档、搜索、提问。

这是一些对你有帮助的资源:

[Array.reduce()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)

[Symmetric Difference](https://www.youtube.com/watch?v=PxffSUQRkG4)

思路：

通读题目，其实就是要求我们把参数数组中的前两项做运算，得到一个所有项都没同时出现在两个数组中的新数组，然后把这个新数组作为首项，继续与后面的数组进行同样操作。

我们第一步得到的参数数组是个二维数组，而函数最后返回的是一个结果，一维数组，很容易就想到Array归并用的 reduce() 方法。

reduce() 传入的函数带有4个参数：前一个值 prev 、当前值 cur 、项的索引 index 、数组对象 array 。

分别对 prev 和 cur 进行过滤，返回对方数组中不存在的值，连接成为新数组。最后对新数组去重。

去重时，可以另写一个函数，像这样：
```javascript
function unique(array){
    var n = [];
    for(var i = 0;i < array.length; i++){
        if(n.indexOf(array[i]) == -1) {
         n.push(array[i]);
        }
    }
    return n;
}
```
也可以在返回结果中继续利用 filter() 去重：

//整个函数的返回值
```javascript
return temp.filter(function(item,index,array){
    return array.indexOf(item) == index;
  });//自身查重只需要让它本身第一次出现在原数组的位置为索引值index，就可以保留且只保留一个。

```
解法：
```javascript
function sym(args) {
  var arr = [];
  for(var i = 0; i < arguments.length; i++){
    arr.push(arguments[i]);
  }
    var temp = arr.reduce(function(prev,cur,index,array){
    var a = prev.filter(function(item){
      return cur.indexOf(item) < 0;
    });
    var b = cur.filter(function(item){
      return prev.indexOf(item) < 0;
    });
    return a.concat(b);
  });
  return temp.filter(function(item,index,array){
    return array.indexOf(item)== index ;
  });
  //自身查重只需要让它本身第一次出现在原数组的位置为索引值index，就可以保留且只保留一个。
  //或者调用外部函数去重；function unique(array)见“思路”部分
  //return unique(temp);
}

sym([1, 2, 3], [5, 2, 1, 4]);

```

