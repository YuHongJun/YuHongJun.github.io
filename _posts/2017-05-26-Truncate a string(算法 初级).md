---
author: Demi_YuHongJun
comments: true
date: 2017-05-26 09:42:32+00:00
layout: post
title: Truncate a string(算法 初级)
description: Truncate a string
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---

https://www.freecodecamp.cn/challenges/truncate-a-string

思路

数组分割成块，看到这个就想到 slice() 方法。 slice() 可接收两个参数，返回项的起始位置、（可选）返回项的结束位置。准确的说，返回的数组是从第一个参数到第二个参数前一个位置的项，也就是说，返回的数组包含起始位置但不包含结束位置。

用 for() 循环迭代传进来的数组，在循环内部用把 slice() 切割的块推入新声明的空数组中，就能达到预期结果啦！
#### 解法一
```javascript
function truncate(str, num) {
  // Clear out that junk in your trunk
  var newStr='';
  if(num<=3){
    newStr= str.slice(0,num)+'...';
  }else if(num>=str.length){
    newStr=str;
  }else{
    newStr= str.slice(0,num-3)+'...';
  }
  
  return  newStr;
}

truncate("A-tisket a-tasket A green and yellow basket",11);

```
