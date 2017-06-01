---
author: Demi_YuHongJun
comments: true
date: 2017-05-31 11:42:32+00:00
layout: post
title: Where art thou（算法）
description: Where art thou（算法）
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---

https://www.freecodecamp.cn/challenges/where-art-thou

写一个 function，它遍历一个对象数组（第一个参数）并返回一个包含相匹配的属性-值对（第二个参数）的所有对象的数组。如果返回的数组中包含 source 对象的属性-值对，那么此对象的每一个属性-值对都必须存在于 collection 的对象中。

例如，如果第一个参数是 [{ first: "Romeo", last: "Montague" }, { first: "Mercutio", last: null }, { first: "Tybalt", last: "Capulet" }]，第二个参数是 { last: "Capulet" }，那么你必须从数组（第一个参数）返回其中的第三个对象，因为它包含了作为第二个参数传递的属性-值对。

如果你被难住了，记得使用 Read-Search-Ask编写你自己的代码。

这是一些对你有帮助的资源:

[Global Object](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object)

[Object.hasOwnProperty()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/hasOwnProperty)

[Object.keys()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/keys)

```javascript
function where(collection, source) {
  var arr = [];
  // What's in a name?
    var keys = Object.keys(source);
  arr = collection.filter(function(item){
    for(var i = 0; i < keys.length; i++){
      if(!item.hasOwnProperty(keys[i]) || item[keys[i]] !== source[keys[i]]){
        return false;
      }    
    }   
    return true;
  });
  return arr;
}

where([{ first: "Romeo", last: "Montague" }, { first: "Mercutio", last: null }, { first: "Tybalt", last: "Capulet" }], { last: "Capulet" });

```

