---
author: Demi_YuHongJun
comments: true
date: 2017-05-23 09:42:32+00:00
layout: post
title: Return Largest Numbers in Arrays(算法 初级)
description: Return Largest Numbers in Arrays(算法 初级)
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---
https://www.freecodecamp.cn/challenges/return-largest-numbers-in-arrays

#### 知识点
[Comparison Operators](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Comparison_Operators)


一、题目描述：
大数组中包含了4个小数组，分别找到每个小数组中的最大值，然后把它们串联起来，形成一个新数组。

```js
largestOfFour([[4, 5, 1, 3], [13, 27, 18, 26], [32, 35, 37, 39], [1000, 1001, 857, 1]]) 应该返回数组 - [5, 27, 39, 1001]
largestOfFour([[13, 27, 18, 26], [4, 5, 1, 3], [32, 35, 37, 39], [1000, 1001, 857, 1]]) 应该返回 -   [27, 5, 39, 1001]
largestOfFour([[4, 9, 1, 3], [13, 35, 18, 26], [32, 35, 97, 39], [1000000, 1001, 857, 1]]) 应该返回 -   [9, 35, 97, 1000000]
```

二、思路分析：

Math.max()方法，支持传递多个参数，比如：Math.max(1,4,2,3,7,5,6)

但是它不支持直接传递一个数组作为参数，比如：Math.max(new Array(1,4,2,3,7,5,6))。

这里，只要我们有方法把数组，一个一个拆分开来，传递到Math.max()方法中，就实现了传递数组的方法。

所有函数都有apply(作用域链,参数)这个方法，这个函数的“参数”，接收一个数组，并且是将数组中的每个值，分开来，传递给调用函数。所以就实现了传递一个数组，取得最大值的方法。

##### apply和call

我首先从网上查到关于apply和call的定义,然后用示例来解释这两个方法的意思和如何去用.  

    apply:方法能劫持另外一个对象的方法，继承另外一个对象的属性.  
  
Function.apply(obj,args)方法能接收两个参数
obj：这个对象将代替Function类里this对象
args：这个是数组，它将作为参数传给Function（args-->arguments）  
  
    call:和apply的意思一样,只不过是参数列表不一样.  
  
Function.call(obj,[param1[,param2[,…[,paramN]]]])
obj：这个对象将代替Function类里this对象
params：这个是一个参数列表

##### apply的一些其他巧妙用法  
  
细心的人可能已经察觉到,在我调用apply方法的时候,第一个参数是对象(this), 第二个参数是一个数组集合,   
  
这个就是apply的一个巧妙的用处,可以将一个数组默认的转换为一个参数列表([param1,param2,param3] 转换为 param1,param2,param3)

这个如果让我们用程序来实现将数组的每一个项,来装换为参数的列表,可能都得费一会功夫,借助apply的这点特性,所以就有了以下高效率的方法:  
  
- Math.max 可以实现得到数组中最大的一项  
  
因为Math.max 参数里面不支持Math.max([param1,param2]) 也就是数组  

```js
但是它支持Math.max(param1,param2,param3…),所以可以根据刚才apply的那个特点来解决 

var max=Math.max.apply(null,array),这样轻易的可以得到一个数组中最大的一项  
```

(apply会将一个数组装换为一个参数接一个参数的传递给方法)  
  
这块在调用的时候第一个参数给了一个null,这个是因为没有对象去调用这个方法,我只需要用这个方法帮我运算,得到返回的结果就行,所以直接传递了一个null过去  
  
- Math.min  可以实现得到数组中最小的一项  
 
```js
同样和 max是一个思想 var min=Math.min.apply(null,array);  
```
- Array.prototype.push 可以实现两个数组合并  
  
同样push方法没有提供push一个数组,但是它提供了push(param1,param,…paramN) 所以同样也可以通过apply来装换一下这个数组,即:  

```js
var arr1=new Array("1","2","3");   
var arr2=new Array("4","5","6");   
Array.prototype.push.apply(arr1,arr2);  
```

也可以这样理解,arr1调用了push方法,参数是通过apply将数组装换为参数列表的集合.  
  
通常在什么情况下,可以使用apply类似Math.min等之类的特殊用法:  
  
一般在目标函数只需要n个参数列表,而不接收一个数组的形式（[param1[,param2[,…[,paramN]]]]）,可以通过apply的方式巧妙地解决这个问题!  

三、代码：

```js
function largestOfFour(arr) {
  var newArr=[];
  for(var i=0;i<arr.length;i++){
    var num =Math.max.apply(null,arr[i]);
    newArr.push(num);
  }
  return newArr;
}

largestOfFour([[4, 5, 1, 3], [13, 27, 18, 26], [32, 35, 37, 39], [1000, 1001, 857, 1]]);
// [5, 27, 39, 1001]
```