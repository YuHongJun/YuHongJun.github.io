---
author: Demi_YuHongJun
comments: true
date: 2017-06-01 12:42:32+00:00
layout: post
title: Missing letters（算法 中级）
description: Missing letters（算法 中级）
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---

https://www.freecodecamp.cn/challenges/missing-letters

从传递进来的字母序列中找到缺失的字母并返回它。

如果所有字母都在序列中，返回 undefined。

如果你被卡住了，记得开大招 Read-Search-Ask。尝试与他人结伴编程、编写你自己的代码。

这是一些对你有帮助的资源:

[String.charCodeAt()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/charCodeAt)

[String.fromCharCode()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/fromCharCode)

解法一：
```javascript
function fearNotLetter(str) {
var arr = str.split("");
  var temp = [];
  var start = str.charCodeAt(0);
  var end = str.charAt(str.length - 1).charCodeAt(0);
  for(var i = start; i < end + 1; i++){
    var item = String.fromCharCode(i);
    if(arr[0] !== item){  
      temp.push(item);
    }else{
      arr.shift();
    }
  }
  if(temp.length === 0){
    return undefined;
  }else{
    return temp.join("");
  }  
}

fearNotLetter("abce");

```

解法二：
```javascript
function fearNotLetter(str) {
  for(var i=0,len=str.length;i<len;i++){  
   var cha = str.charCodeAt(i+1)-str.charCodeAt(i);  
   if(cha>1){  
     return String.fromCharCode(str.charCodeAt(i)+1);  
   }  
 }  
  return undefined;  
}

fearNotLetter("abce");

```
解法三：

```javascript
function fearNotLetter(str) {
 var first = str.charCodeAt(0);     //把第一个字母的Unicode值单独保存

  for (var i = 0; i < str.length;i++) {     //遍历str字符串

    if(str.indexOf(String.fromCharCode(first + i)) < 0){     //从first开始一个个对str字符串查找，如果找到缺少的那一个，即 <0，则返回该值。

      return String.fromCharCode(first + i);

    }    

  }

  return undefined;      //如果没有发现缺值，则返回undefined。
 
}

fearNotLetter("abce");

```

