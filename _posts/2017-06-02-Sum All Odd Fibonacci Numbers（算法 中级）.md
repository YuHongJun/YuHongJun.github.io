---
author: Demi_YuHongJun
comments: true
date: 2017-06-02 14:42:32+00:00
layout: post
title: Sum All Odd Fibonacci Numbers（算法 中级）
description: Sum All Odd Fibonacci Numbers（算法 中级）
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---

https://www.freecodecamp.cn/challenges/sum-all-odd-fibonacci-numbers

给一个正整数num，返回小于或等于num的斐波纳契奇数之和。

斐波纳契数列中的前几个数字是 1、1、2、3、5 和 8，随后的每一个数字都是前两个数字之和。

例如，sumFibs(4)应该返回 5，因为斐波纳契数列中所有小于4的奇数是 1、1、3。

提示：此题不能用递归来实现斐波纳契数列。因为当num较大时，内存会溢出，推荐用数组来实现。

参考文档：[博客园](http://www.cnblogs.com/meteoric_cry/archive/2010/11/29/1891241.html)，[Issue](https://github.com/FreeCodeCampChina/freecodecamp.cn/issues/19)

如果你被卡住了，记得开大招 Read-Search-Ask。尝试与他人结伴编程、编写你自己的代码。

这是一些对你有帮助的资源:

[Remainder](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Arithmetic_Operators#Remainder_(.25))

解法一：

思路

首先，我们需要一个斐波那契数列衍生的子数组。它的初始值就是斐波那契数列的前两项：

`var fibo = [1, 1];`

我们还需要一个变量来记载当前奇数项的和：

`var oddSum = 2;`

用 while(true) 创建一个循环，在循环中求函数的返回值。
```
while(true){
    //do something...
}
```
设置变量 item ，它的值是下一个斐波那契数的值。

`var item = fibo[0] + fibo[1];`

看题目要求，“返回所有小于传入数值的斐波那契数列中的奇数之和，如果传入的数值是斐波那契数，那么它也应该参与求和”。如果传入的 num 大于或等于下一个将要经历的斐波那契数的话，循环将继续执行。也就是说，如果 num 小于下一个斐波那契数 item ，循环将停止，整个函数返回 oddSum 。
```
if(num < item){
      return oddSum;
    }
```
当下一个斐波那契数 item 是奇数的话，把它加到 oddSum 中：
```
if(item % 2){
      oddSum += item;    
    }
```
其中， item % 2 得出结果是 Number 类型的，如果值为 +0, -0 或 NaN 时，在转为 Boolean 类型时会转为false。也就是说，这个条件语句在 item 为奇数时执行。

最后，更新数组。
```
fibo[0] = fibo[1];
fibo[1] = item;
```
完整解法：
```javascript
function sumFibs(num) {
  var fibo = [1, 1];
  var oddSum = 2;
  while(true){
    var item = fibo[0] + fibo[1];
    if(num < item){
      return oddSum;
    }
    if(item % 2){
      oddSum += item;    
    }
    fibo[0] = fibo[1];
    fibo[1] = item;
  }
}

sumFibs(4);

```

解法二：
```javascript
var sumFibs = function() {
    var cache = [1, 1];
    return function (n) {
        if (n >= cache.length) {
            for (var i = cache.length; i < n ; i++ ) {
                cache[i] = cache[i - 2] + cache[i - 1];
            }
        }
        var arr=cache.filter(function(val){
           return val%2!==0&&val<=n;
         });
        return arr.reduce(function(pre,next){
          return pre+next;
        });
    };
}();
sumFibs(4);

```