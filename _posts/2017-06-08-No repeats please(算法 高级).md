---
author: Demi_YuHongJun
comments: true
date: 2017-06-08 05:42:32+00:00
layout: post
title: No repeats please(算法 高级)
description: No repeats please(算法 高级)
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---
https://www.freecodecamp.cn/challenges/no-repeats-please

把一个字符串中的字符重新排列生成新的字符串，返回新生成的字符串里没有连续重复字符的字符串个数.连续重复只以单个字符为准

例如, `aab` 应该返回 `2` 因为它总共有6种排列 `(aab, aab, aba, aba, baa, baa)`, 但是只有两个 `(aba and aba)`没有连续重复的字符 (在本例中是 `a`).

当你遇到困难的时候，记得查看错误提示、阅读文档、搜索、提问。

这是一些对你有帮助的资源:

[Permutations](https://www.mathsisfun.com/combinatorics/combinations-permutations.html)

[RegExp](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp)

```javascript
function permAlone(str) {
  
//create variable to store number of perms without a repeat
var noDupes = 0;
 
//split string into array
var strArray = str.split("");
  
// Call with an array of the original string
findPerm(strArray.length, strArray);
  
return noDupes;
 
//Heap's Algorithm
function findPerm(n, arr) {
    // If only 1 element, just output the array
    
    if (n == 1) {
//check for duplicates
    if(!(/([a-zA-Z])\1+/).test(arr.join(""))){
        noDupes += 1;
        }
      return;
    }
 
    for (var i = 0; i < n; i+= 1) {
        findPerm(n - 1, arr);
 
        // If n is even
        if (n % 2 === 0) {
            swap(i, n - 1);
        } else {
            swap(0, n - 1);
        }
    }
 
 function swap(idxA, idxB) {
    var tmp = arr[idxA];
    arr[idxA] = arr[idxB];
    arr[idxB] = tmp;
    }
  }
}
 
//call permAlone() with any string
permAlone('aab');

```