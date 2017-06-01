---
author: Demi_YuHongJun
comments: true
date: 2017-05-27 09:42:32+00:00
layout: post
title: Mutations(算法 初级)
description: Mutations(算法 初级)
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---

https://www.freecodecamp.cn/challenges/mutations

蛤蟆可以吃队友，也可以吃对手。

如果数组第一个字符串元素包含了第二个字符串元素的所有字符，函数返回true。

举例，["hello", "Hello"]应该返回true，因为在忽略大小写的情况下，第二个字符串的所有字符都可以在第一个字符串找到。

["hello", "hey"]应该返回false，因为字符串"hello"并不包含字符"y"。

["Alien", "line"]应该返回true，因为"line"中所有字符都可以在"Alien"找到。

当你完成不了挑战的时候，记得开大招'Read-Search-Ask'。

解法
```javascript
function mutation(arr) {
 var main= arr.join(',').toLowerCase();
  var search= main.split(',');
  for(var a in search[1]){
    if( search[0].indexOf(search[1][a])==-1){
      return false;
    }
  }
  return true;
}
mutation(["hello", "hey"]);
```