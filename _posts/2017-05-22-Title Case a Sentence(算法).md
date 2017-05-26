---
author: Demi_YuHongJun
comments: true
date: 2017-05-22 09:42:32+00:00
layout: post
title: Title Case a Sentence(算法)
description: Title Case a Sentence(算法)
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---

https://www.freecodecamp.cn/challenges/title-case-a-sentence


```javascript
function titleCase(str) {
 var newStr= str.split(" ");
  for(var i=0;i<newStr.length;i++){
    if(newStr[i]==="") continue;
    var copy =newStr[i].slice(1).toLowerCase();
    newStr[i]=newStr[i][0].toUpperCase()+copy;
  }
  newStr=newStr.join(" ");
  return newStr;
}
titleCase("sHoRt AnD sToUt");
```




#### slice,substr和substring的区别

首先，他们都接收两个参数，slice和substring接收的是起始位置和结束位置(不包括结束位置)，而substr接收的则是起始位置和所要返回的字符串长度。直接看下面例子：
```
1     var test = 'hello world';
2 
3     alert(test.slice(4,7));             //o w
4     alert(test.substring(4,7));         //o w
5     alert(test.substr(4,7));            //o world

```

这里有个需要注意的地方就是：substring是以两个参数中较小一个作为起始位置，较大的参数作为结束位置。

如：


```alert(test.substring(7,4));          //o w```

接着，当接收的参数是负数时，slice会将它字符串的长度与对应的负数相加，结果作为参数；substr则仅仅是将第一个参数与字符串长度相加后的结果作为第一个参数；substring则干脆将负参数都直接转换为0。测试代码如下：

```
1     var test = 'hello world';
2 
3     alert(test.slice(-3));         //rld
4     alert(test.substring(-3));     //hello world
5     alert(test.substr(-3));        //rld

6     alert(test.slice(3,-4));       //lo w
7     alert(test.substring(3,-4));   //hel
8     alert(test.substr(3,-4));      //空字符串
```

**注意：IE对substr接收负值的处理有错，它会返回原始字符串。**