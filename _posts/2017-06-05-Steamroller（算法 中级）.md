---
author: Demi_YuHongJun
comments: true
date: 2017-06-05 09:42:32+00:00
layout: post
title: Steamroller（算法 中级）
description: Steamroller（算法 中级）
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---

https://www.freecodecamp.cn/challenges/steamroller

对嵌套的数组进行扁平化处理。你必须考虑到不同层级的嵌套。

如果你被卡住了，记得开大招 Read-Search-Ask。尝试与他人结伴编程、编写你自己的代码。

这是一些对你有帮助的资源:

[Array.isArray()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/isArray)

解法：
```javascript
function steamroller(arr) {
  // I'm a steamroller, baby
  var brr=[];
    function flat(puzzle){
      for(var i =0;i<puzzle.length;i++){
        if(Array.isArray(puzzle[i])){
          flat(puzzle[i]);
        }else{
          brr.push(puzzle[i]);
       }
     }
   }
   flat (arr);
   return brr;
}

steamroller([1, [2], [3, [[4]]]]);

```

易错点与收获

易错点1：Array.isArray()方法应用错误，误以为是像reduce,filter方法一样是数组实例的方法，其实这是数组原型的方法，所以要判断的数组实例应该作为参数放在括号里，而不是作为对象去应用该方法。作为参数而非对象。

收获1：return语句的加深理解。我一开始在if语句的第一个代码块里写的是return flat(puzzle(i));，然后一直不能通过，并且得到的结果只有数组里的第一项，后面的都没有。删掉return之后就通过了。原因其实比较简单，我开始只知道return语句在结束当前代码后会移交控制权，但并不清楚会到底移交给谁，移交到什么位置，但经过这个例子，很明显不是跳出if语句，也不是跳出for循环，而是直接跳出了当前函数。通过查阅高程可知，return语句是专用于函数里的语句，一个函数在执行过程中只要遇到return就会立即返回return后面的值并退出当前函数，return是函数特有的语句，所以是以函数为单位进行退出的，函数的返回值即return后面跟的值，若没有return语句会返回undefined。

收获2：for循环是我最喜欢也是最常用的语句，但其实写起来真是挺烦的，for循环仅仅只是一种迭代的主式而已，数组的迭代方法有很多现成的可以用，高程第96页说到ES5中数组有5个迭代方法：every(),filter(),forEach(),map(),some()。每个方法都接收两个参数，第一个参数为回调函数（必选），第二个参数为作用域对象，用来绑定this值的（可选）。every()和some()是用来判断数组的，测试某个数组能否通过某项测试，因为它们都返回布尔值。filter()和map()都是处理数组的，它们都返回数组，前者返回测试通过的数组项，后者返回每次函数调用的结果组成的数组。而forEach()方法就是今天的主角，可以当作for循环来使用的，它对数组中的每一项运行给定函数，没有返回值。
