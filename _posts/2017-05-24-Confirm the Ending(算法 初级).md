---
author: Demi_YuHongJun
comments: true
date: 2017-05-24 09:42:32+00:00
layout: post
title: Confirm the Ending(算法 初级)
description: Confirm the Ending(算法 初级)
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---

https://www.freecodecamp.cn/challenges/confirm-the-ending

检查一个字符串(str)是否以指定的字符串(target)结尾。

如果是，返回true;如果不是，返回false。

#### 解法1
```
function confirmEnding(str, target) {
  // "Never give up and good luck will find you."
  // -- Falcor
    if ( str.substr(str.length-target.length , str.length) === target) {
    return true;
  }else {
    return false;
  }
  return str;
}

confirmEnding("Bastian", "n");

```

#### 解法2
```
function confirmEnding(str, target) {
  // "Never give up and good luck will find you."
  // -- Falcor
    if ( str.slice(str.length-target.length , str.length) === target) {
    return true;
  }else {
    return false;
  }
  return str;
}

confirmEnding("Bastian", "n");

```

#### 解法3

```
function confirmEnding(str, target) {
  // "Never give up and good luck will find you."
  // -- Falcor
    if ( str.substring(str.length-target.length , str.length) === target) {
    return true;
  }else {
    return false;
  }
  return str;
}

confirmEnding("Bastian", "n");

```

三种方法都是截取字符串指定字段，其中slice()和substring()接收的是起始位置和结束位置(不包括结束位置)，而substr接收的则是起始位置和所要返回的字符串长度.

还有在对负值的处理上，slice()会将它字符串的长度与对应的负数相加，结果作为参数；substr()则仅仅是将第一个参数与字符串长度相加后的结果作为第一个参数；substring()则干脆将负参数都直接转换为0。