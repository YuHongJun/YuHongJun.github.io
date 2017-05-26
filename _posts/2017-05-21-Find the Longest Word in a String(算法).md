---
author: Demi_YuHongJun
comments: true
date: 2017-05-21 09:42:32+00:00
layout: post
title: Find the Longest Word in a String(算法)
description: Find the Longest Word in a String
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---
https://www.freecodecamp.cn/challenges/find-the-longest-word-in-a-string

### 知识点
[Array.prototype.reduce()](https://developer.mozilla.org/cn/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce?v=example)

```javascript
function findLongestWord(str) {
  var arr= str.replace(/[^A-Za-z\s]/g,"").split(" ");
 var longestWord=arr.reduce(function(prev,curr){
   return prev.length>curr.length?prev:curr;
 },"");
  
  return longestWord.length;
}

findLongestWord("The quick brown fox jumped over the lazy dog");

```

