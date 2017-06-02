---
author: Demi_YuHongJun
comments: true
date: 2017-06-02 09:42:32+00:00
layout: post
title: Sum All Primes(算法 中级)
description: Sum All Primes(算法 中级)
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---

https://www.freecodecamp.cn/challenges/sum-all-primes

求小于等于给定数值的质数之和。

只有 1 和它本身两个约数的数叫质数。例如，2 是质数，因为它只能被 1 和 2 整除。1 不是质数，因为它只能被自身整除。

给定的数不一定是质数。

如果你被卡住了，记得开大招 Read-Search-Ask。尝试与他人结伴编程、编写你自己的代码。

这是一些对你有帮助的资源:

[For Loops](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/for)

[Array.push()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/push)

解法一：

思路

这题主要有两个逻辑，一个是判断一个数是否为质数，一个是求和。我们一个一个来。

首先，判断一个数是否为质数。创建函数 ifPrime(num) ，如果返回 true，则传入参数 num 为质数；返回 false 则该数为合数（不是质数）。
```javascript
var ifPrime = function(num){
    if(num < 2){
        return false;
    }
    for(var i = 2; i < num; i++){
        if(num % i === 0){
            return false;
        }
    }
    return true;
};

```
这段代码的逻辑有两个：其一，小于 2 的都不是质数。这个很容易理解，因为大家都知道 2 是最小的质数。其二，创建循环，让有其它因子的数返回 false。我们知道，质数有两个因子，1 和它本身。也就是说，一个质数在大于一且小于其自身的范围内是不能有其它因子的。如果这个范围内的数有能被传进来的 num 整除的，说明能被整除的数为合数。除此以外，都为质数，函数将返回 true。

到这里，这段代码我们写起来容易，但后台运算起来就有点麻烦了。我们能不能做点事情，使得运算量减少，效率更高一些呢？答案是 YES。

偶数至少有一个因子 2，除了 2 以外的偶数一定不是质数。因此，我们可以这样改进我们的循环：
```javascript
var ifPrime = function(num){
      if (num < 2) return false;
      if (num === 2||num === 3) return true;
      if (num % 2 === 0||num % 3 === 0) return false;
    for(var i = 3; i < num; i+=2){
        if(num % i === 0){
            return false;
        }
    }
    return true;
  };
```
注意第二个和第三个 if 的先后顺序一定不能错哦，因为 2 、3也是质数。

对一个正整数 num，它的平方根为 √num。假设它是一个合数，可被分解为 num = x * y 形式，又因为 num = √num * √num，如果在 0~ √num 范围内都没能找到 num 的因子，即 x > √num 且 y > √num，易知在 √num ~ num 范围内也不会找到 num 的因子的，因为 x * y 一定大于 num。也就是说，num 是一个质数。

总结上面的推理，一个数的平方根之前若（除 1 之外）找不到因子的话，则该数为质数。

说了这么多，其实是想进一步优化上面的循环啦：
```javascript
for(var i = 3; i <= Math.sqrt(num); i+=2){
    if(num % i === 0){
        return false;       
    }
}
```
完整解法：
```javascript
function sumPrimes(num) {
  var arr = [];
  var ifPrime = function(num){
    if (num < 2) return false;
    if (num === 2||num === 3) return true;
    if (num % 2 === 0||num % 3 === 0) return false;
    for(var i = 3; i <= Math.sqrt(num); i+=2){
      if(num % i === 0){
        return false;
      }
    }
    return true;
  };
  for(var i = 2; i <= num; i++){
    if(ifPrime(i)){
      arr.push(i);
    }
  }
  return arr.reduce(function(prev,cur,index,array){
     return prev + cur;
  },0);
}

sumPrimes(10);


```

