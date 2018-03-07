---
author: Demi_YuHongJun
comments: true
date: 2017-05-17 09:42:32+00:00
layout: post
title: Task 2 - Valid Parentheses
description: Task 2 - Valid Parentheses
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

Your task is to write a function that takes a string of parentheses, and determines if the order of the parentheses is valid. The function should return true if the string is valid, and false if it's invalid.

  "()"              =>  true
  ")(()))"          =>  false
  "("               =>  false
  "(())((()())())"  =>  true


#### Answer

```
const isValid = (s) => {
    let len = s.length;
    let stack = [];
    if (len === 0 || len%2 !== 0){
        return false;
    }
    s = s.replace(/\(/g,"1");
    s = s.replace(/\)/g,"4");
    stack.push(s[0]);
    for(var i = 1; i<len; i++){
        if(parseInt(s[i])-stack[stack.length-1] === 3){
            stack.pop();
        }else{
            stack.push(s[i]);
        }
    }
    console.log(stack);
    if(stack.length === 0)
        return true;
    else
        return false;
};
isValid('()')
isValid(')(()))')
isValid('(')
isValid('(())((()())())')
```


