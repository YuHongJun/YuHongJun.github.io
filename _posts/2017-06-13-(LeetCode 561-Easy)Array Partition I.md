---
author: Demi_YuHongJun
comments: true
date: 2017-06-13 04:42:32+00:00
layout: post
title: (LeetCode 561-Easy)Array Partition I
description: (LeetCode 561-Easy)Array Partition I
keywords: LeetCode
categories:
- Tech
tags:
- LeetCode
---
* 目录
{:toc}
---

https://leetcode.com/problems/array-partition-i

##### Description
Given an array of 2n integers, your task is to group these integers into n pairs of integer, say (a1, b1), (a2, b2), ..., (an, bn) which makes sum of min(ai, bi) for all i from 1 to n as large as possible.

Example 1:
```
Input: [1,4,3,2]

Output: 4
Explanation: n is 2, and the maximum sum of pairs is 4 = min(1, 2) + min(3, 4).
```
Note:
1. n is a positive integer, which is in the range of [1, 10000].
2. All the integers in the array will be in the range of [-10000, 10000].

问题分析：

由题意可知，我们可以将整个数组升序排序，每两个数为一组，取其最小的那个值相加，最终得到答案。

javascript:
```
/**
 * @param {number[]} nums
 * @return {number}
 */
var arrayPairSum = function(nums) {
    var len = nums.length,
    total = nums.sort((x,y)=>x-y),
    sum=0;
    
    do {
        sum +=total[len-2];
    } while (len-=2);
 
    return sum;
    
};
```



python:
```
class Solution(object):

    def arrayPairSum(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        return sum(sorted(nums)[::2])

```

```
class Solution(object):
    def arrayPairSum(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        
        nums.sort()
        return sum(nums[::2])
```
