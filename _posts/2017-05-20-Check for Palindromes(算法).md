---
author: Demi_YuHongJun
comments: true
date: 2017-05-20 09:42:32+00:00
layout: post
title: Check for Palindromes(算法)
description: Check for Palindromes(算法)
keywords: FreeCodeCamp, fcc
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---
#### 原题目
 https://www.freecodecamp.cn/challenges/check-for-palindromes
 
 Palindromes称之为回文。在中文文当中是指倒着念和顺着念都是相同的，前后对称，例如“上海自来水来自海上”。在英文文当中是指正着看和反着看都相同的单词，例如“madam”。而对于数字，又称之为回文数，是指一个像“16461”这样的对称的数，即这个数的数字按相反的顺序重新排列后得到的数和原来的数一样。
 
 在JavaScript中Palindromes也常出现在一些算法题中，这篇文章主要介绍如何使用JavaScript判断一个字符是不是Palindromes。
 
#### 算法
判断给定的字符串，如果字符串是一个Palindromes，那么返回true，反之返回false
Palindromes是一个词或一个名子，在忽略标点符号和间距之下，前后指写方式相同
#### 测试用例

>palindrome("eye") 应该返回一个布尔值<br/>
palindrome("eye") 应该返回 true.<br/>
palindrome("race car") 应该返回 true.<br/>
palindrome("not a palindrome") 应该返回 false.<br/>
palindrome("A man, a plan, a canal. Panama") 应该返回 true.<br/>
palindrome("never odd or even") 应该返回 true.<br/>
palindrome("nope") 应该返回 false.<br/>
palindrome("almostomla") 应该返回 false.<br/>
palindrome("My age is 0, 0 si ega ym.") 应该返回 true.<br/>
palindrome("1 eye for of 1 eye.") 应该返回 false.<br/>
palindrome("0_0 (: /-\ :) 0-0") 应该返回 true.<br/>

其中palindrome()是一个我们将要定义的函数，并且给这个函数传入一个str参数，如果str是一个Palindromes，将返回的是true，反之返回的是false。

#### 知识点
在后面的介绍中，将会用到的一些JavaScript知识点:

0. [正则表达式](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Regular_Expressions)
1. [String.replace()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/replace)
2. [String.toLowerCase()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/toLowerCase)
3. [String.split()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/split)
4. [Array.reverse()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse)
5. [Array.join()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/join)
6. [String.length()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/length)
7. [for](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/for)

在这篇文章中主要用到下面两个正则表达式：

```
/[^A-Za-z0–9]/g 
 或
/[\W_]/g
```

#### 实现方法
检测一个字符串是不是Palindrome，方法不仅仅是一种，接下来看看网上介绍的几种方法：
##### 方法1
```
function palindrome(str) {
  // Good luck!
  var re=/[\W_]/g;
  var lowRegStr=str.replace(re,'').toLowerCase();
  var len =lowRegStr.length;
  for(var i=0,halfLen=len/2;i<halfLen;i++){
    if(lowRegStr[i]!= lowRegStr[len-1-i]){
      return false;
    }
  }
  return true;
}

palindrome("My age is 0, 0 si ega ym.");
```

#### 方法2
```
function palindrome(str) {
  // Good luck!
  var re=/[\W_]/g;
  var lowRegStr=str.replace(re,'').toLowerCase();
 
  var reverseStr=lowRegStr.split('').reverse().join('');

  return reverseStr === lowRegStr;
}



palindrome("My age is 0, 0 si ega ym.");

```