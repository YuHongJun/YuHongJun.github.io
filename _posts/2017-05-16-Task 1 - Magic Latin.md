---
author: Demi_YuHongJun
comments: true
date: 2017-05-16 09:42:32+00:00
layout: post
title: Task 1 - Magic Latin
description: Task 1 - Magic Latin
keywords: FreeCodeCamp, fcc
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---
#### Question

Your task is move the first letter of each word to the end of it, then add "ay" to the end of the word. Leave punctuation marks untouched.

  magicLatin('Magic latin is cool'); // agicMay atinlay siay oolcay
  magicLatin('Hello world !');     // elloHay orldWay !

#### Answer
```
const magicLatin = (str) => {
  let comstr = "";
  let arr = str.split(" ");
  for (let i = 0; i < arr.length; i++) {
    arr[i] = arr[i] + arr[i][0] + "ay";
    arr[i] = arr[i].substring(1);
    comstr = comstr + arr[i] + " ";
  }
  document.write(comstr + "<br>");
}

 magicLatin('Magic latin is cool');
 magicLatin('Hello world !');
```



