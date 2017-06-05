---
author: Demi_YuHongJun
comments: true
date: 2016-06-05 14:42:32+00:00
layout: post
title: Arguments Optional(算法 中级)
description: Arguments Optional(算法 中级)
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---

https://www.freecodecamp.cn/challenges/arguments-optional

创建一个计算两个参数之和的 function。如果只有一个参数，则返回一个 function，该 function 请求一个参数然后返回求和的结果。

例如，add(2, 3) 应该返回 5，而 add(2) 应该返回一个 function。

调用这个有一个参数的返回的 function，返回求和的结果：

var sumTwoAnd = add(2);

sumTwoAnd(3) 返回 5。

如果两个参数都不是有效的数字，则返回 undefined。

如果你被卡住了，记得开大招 Read-Search-Ask。尝试与他人结伴编程、编写你自己的代码。

这是一些对你有帮助的资源:

[Closures](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Closures)

[Arguments object](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/arguments)

思路

先让不符合条件的值返回 undefined：
```javascript
if(typeof arguments[0] !== "number" || 
    (arguments.length > 1 && typeof arguments[1] !== "number")){
    return undefined;
}
```
本解法中，只有两种情况，一种是传入参数为一个，另一种是传入参数为两个（或以上）。

在第二种情况中，当传入参数为多个时，也只会返回前两个参数的和。

解法一：
```javascript
function add() {
if(typeof arguments[0] !== "number" || (arguments.length > 1 && typeof arguments[1] !== "number")){
    return undefined;
  }
  if(arguments.length == 1){
    var arg0 = arguments[0];
    return function(num){
      if(typeof num !== "number"){
        return undefined;
      }
      return arg0 + num;
    };
  }else{
    return arguments[0] + arguments[1];
  }
}

add(2)(3);

```
解法二：
```javascript
function add() {
//typeof 返回对象的类型(总共有5种类型：null、number、string、boolean、undefined)
  //arguments[i]返回函数add中传入的dii个参数
  if(typeof arguments[0]=="number" && typeof arguments[1]=="number"){
    return arguments[0]+arguments[1];
  }
  else if(arguments.length==1 && typeof arguments[0]=="number"){
    var x=arguments[0];
    //如果只有一个数字型参数x，返回x和后面捕捉到的任意一个数字型参数y之和
    return function(y){
      if(typeof y =="number"){
        return x+y;
      }
    };
  }
}

add(2)([3]);

```