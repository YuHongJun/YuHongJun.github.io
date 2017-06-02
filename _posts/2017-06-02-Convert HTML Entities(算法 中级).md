---
author: Demi_YuHongJun
comments: true
date: 2017-06-02 09:42:32+00:00
layout: post
title: Convert HTML Entities(算法 中级)
description: Convert HTML Entities(算法 中级)
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---

https://www.freecodecamp.cn/challenges/convert-html-entities

将字符串中的字符 &、<、>、" （双引号）, 以及 ' （单引号）转换为它们对应的 HTML 实体。

如果你被卡住了，记得开大招 Read-Search-Ask。尝试与他人结伴编程、编写你自己的代码。

这是一些对你有帮助的资源:

[RegExp](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp)

[HTML Entities](https://dev.w3.org/html5/html-author/charref)

```javascript
function convert(str) {
  // &colon;&rpar;
 return str.replace(/[&<>"']/g, function(match) {//match or $0
        return "&" + {"&":"amp", "<":"lt", ">":"gt", '"':"quot", "'":"apos"}[match] + ";";
    });
}

convert("Dolce & Gabbana");


```