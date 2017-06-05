---
author: Demi_YuHongJun
comments: true
date: 2017-06-05 13:42:32+00:00
layout: post
title: Everything Be True（算法 中级）
description: Everything Be True（算法 中级）
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---

https://www.freecodecamp.cn/challenges/everything-be-true

所有的东西都是真的！

完善编辑器中的every函数，如果集合(collection)中的所有对象都存在对应的属性(pre)，并且属性(pre)对应的值为真。函数返回ture。反之，返回false。

记住：你只能通过中括号来访问对象的变量属性(pre)。

提示：你可以有多种实现方式，最简洁的方式莫过于[Array.prototype.every()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/every)。

如果你被卡住了，记得开大招 Read-Search-Ask。尝试与他人结伴编程、编写你自己的代码。

思路:

这里用到了一个数组的迭代方法 every() 。该方法将传入一个函数，当每一项均返回 true 时，该函数才返回 true。

解法一:
```javascript
function every(collection, pre) {
  // Is everyone being true?
  var result= collection.every(function(item){
      return item[pre];
  });
  return result;
}

every([{"user": "Tinky-Winky", "sex": "male"}, {"user": "Dipsy", "sex": "male"}, {"user": "Laa-Laa", "sex": "female"}, {"user": "Po", "sex": "female"}], "sex");

```
解法二：
```javascript
function every(collection, pre) {
  // Is everyone being true?
  for(var i in collection){
    if(!collection[i][pre]){
      return false;
    }
  }
  return true;
}

every([{"user": "Tinky-Winky", "sex": "male"}, {"user": "Dipsy", "sex": "male"}, {"user": "Laa-Laa", "sex": "female"}, {"user": "Po", "sex": "female"}], "sex");

```