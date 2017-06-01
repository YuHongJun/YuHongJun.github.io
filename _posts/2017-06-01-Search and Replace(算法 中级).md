---
author: Demi_YuHongJun
comments: true
date: 2017-06-01 09:42:32+00:00
layout: post
title: Search and Replace(算法 中级)
description: Search and Replace(算法 中级)
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---

https://www.freecodecamp.cn/challenges/search-and-replace

使用给定的参数对句子执行一次查找和替换，然后返回新句子。

第一个参数是将要对其执行查找和替换的句子。

第二个参数是将被替换掉的单词（替换前的单词）。

第三个参数用于替换第二个参数（替换后的单词）。

注意：替换时保持原单词的大小写。例如，如果你想用单词 "dog" 替换单词 "Book" ，你应该替换成 "Dog"。

如果你被难住了，记得使用 Read-Search-Ask尝试与他人结伴编程、编写你自己的代码。

这是一些对你有帮助的资源:

[Array.splice()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)

[String.replace()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/replace)

[Array.join()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/join)

解法:
```javascript
function myReplace(str, before, after) {
 var re=/^[A-Z]/;
 if(re.test(before.charAt(0))) {
   after=after.charAt(0).toUpperCase()+after.slice(1);
 }
  str=str.replace(before,after);
  return str;
}

myReplace("A quick brown fox jumped over the lazy dog", "Jumped", "leaped");

```


