---
author: Demi_YuHongJun
comments: true
date: 2017-06-01 09:42:32+00:00
layout: post
title: DNA Pairing(算法 中级)
description: DNA Pairing(算法 中级)
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---
https://www.freecodecamp.cn/challenges/dna-pairing

DNA 链缺少配对的碱基。依据每一个碱基，为其找到配对的碱基，然后将结果作为第二个数组返回。

[Base pairs（碱基对）](https://en.wikipedia.org/wiki/Base_pair) 是一对 AT 和 CG，为给定的字母匹配缺失的碱基。

在每一个数组中将给定的字母作为第一个碱基返回。

例如，对于输入的 GCG，相应地返回 [["G", "C"], ["C","G"],["G", "C"]]

字母和与之配对的字母在一个数组内，然后所有数组再被组织起来封装进一个数组。

如果你被卡住了，记得开大招 Read-Search-Ask。尝试与他人结伴编程、编写你自己的代码。

这是一些对你有帮助的资源:

[Array.push()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/push)

[String.split()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/split)

解法：
```javascript
function pair(str) {
 var arr = str.split("");
  var pair = "";
  var result = arr.map(function(item,index,array){
    if(item === "A"){
      pair = "T";
    }else if(item === "T"){
      pair = "A";
    }else if(item === "C"){
      pair = "G";
    }else if(item === "G"){
      pair = "C";
    }
    return [item,pair];
  });
  return result;
}

pair("GCG");

```
