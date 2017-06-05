---
author: Demi_YuHongJun
comments: true
date: 2017-06-05 12:42:32+00:00
layout: post
title: Binary Agents(算法 中级)
description: Binary Agents(算法 中级)
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---

https://www.freecodecamp.cn/challenges/binary-agents

传入二进制字符串，翻译成英语句子并返回。

二进制字符串是以空格分隔的。

如果你被卡住了，记得开大招 Read-Search-Ask。尝试与他人结伴编程、编写你自己的代码。

这是一些对你有帮助的资源:

[String.charCodeAt()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/charCodeAt)

[String.fromCharCode()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/fromCharCode)

思路

把传进来的字符串用空格切割为数组。遍历数组每一项，把二进制转为十进制之后用 String.fromCharCode() 方法得到对应的字符。

最后把数组重新连接成字符串，搞定。

解法：
```javascript
function binaryAgent(str) {
 var arr = str.split(" ");
  var result = arr.map(function(item){
    return String.fromCharCode(parseInt(item,2));
  });
  
  return result.join("");
}

binaryAgent("01000001 01110010 01100101 01101110 00100111 01110100 00100000 01100010 01101111 01101110 01100110 01101001 01110010 01100101 01110011 00100000 01100110 01110101 01101110 00100001 00111111");

```
