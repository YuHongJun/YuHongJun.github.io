---
author: Demi_YuHongJun
comments: true
date: 2017-05-18 09:42:32+00:00
layout: post
title: Task 3 - Binary number divisible by 5
description: Task 3 - Binary number divisible by 5
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

You need to define a regular expression which tests if a given string representing a binary number is divisible by 5.

  // 5 divisable by 5
  divisibleByFive.test('101') === true
  // 135 divisable by 5
  divisibleByFive.test('10000111') === true
  // 666 not divisable by 5
  divisibleByFive.test('0000001010011010') === false


#### Answer

```
const testReg = (value) => {
  const re =/^(0|1(10)*(0|11)(01*01|01*00(10)*(0|11))*1)$/
  const result = re.test(value)
  console.log(result);
}
testReg('101')
testReg('10000111')
testReg('0000001010011010')


```


