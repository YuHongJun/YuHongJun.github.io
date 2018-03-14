---
author: Demi_YuHongJun
comments: true
date: 2017-05-19 09:42:32+00:00
layout: post
title: Task 4 - Next bigger number
description: Task 4 - Next bigger number
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
You have to create a function that takes a positive integer number and returns the next bigger number formed by the same digits:

  nextBigger(12) == 21
  nextBigger(513) == 531
  nextBigger(2017) == 2071
  nextBigger(111) == -1
  nextBigger(531) == -1


#### Answer

```
function nextBigger(n) {
  const [left, right] = splitDigits(`${n}`.split(''), 2)
  if (!left) return -1
  return Number(left.concat(resort(right)).join(''))
}

function splitDigits(digits, rightSize) {
  if (rightSize > digits.length) return []
  const right = digits.slice(-rightSize)
  if (right[0] < right[1]) return [digits.slice(0, -rightSize), right]
  return splitDigits(digits, rightSize + 1)
}

function resort(right) {
  const first = right[0]
  const rest = right.slice(1).sort()
  const idx = rest.findIndex(n => n > first)
  const p = rest[idx]
  rest[idx] = first
  return [p].concat(rest)
}
nextBigger(12)
nextBigger(513)
nextBigger(2017)
nextBigger(111)
nextBigger(531)
```


