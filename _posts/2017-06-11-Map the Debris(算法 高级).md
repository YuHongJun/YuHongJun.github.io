---
author: Demi_YuHongJun
comments: true
date: 2017-06-11 04:42:32+00:00
layout: post
title: Map the Debris(算法 高级)
description: Map the Debris(算法 高级)
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---

https://www.freecodecamp.cn/challenges/map-the-debris

返回一个数组，其内容是把原数组中对应元素的平均海拔转换成其对应的轨道周期.

原数组中会包含格式化的对象内容，像这样 {name: 'name', avgAlt: avgAlt}.

至于轨道周期怎么求，戳这里 [on wikipedia ](https://en.wikipedia.org/wiki/Orbital_period)(不想看英文的话可以自行搜索以轨道高度计算轨道周期的公式).

求得的值应该是一个与其最接近的整数，轨道是以地球为基准的.

地球半径是 6367.4447 kilometers, 地球的GM值是 398600.4418, 圆周率为Math.PI

当你遇到困难的时候，记得查看错误提示、阅读文档、搜索、提问。

这是一些对你有帮助的资源:

[Math.pow()](https://www.freecodecamp.cn/challenges/map-the-debris)

>GM: Standard gravitational parameter of the central body (provided to us)

>Average distance between the satellite and the centre of the central body.

T=2π√(a^3/GM),a为椭圆长半轴.

Orbital Period = 2 * π * √(avgDist³ / GM)

In JavaScript, it would look like so:

JavaScript
```
var orbitalPeriod = 2 * Math.PI * Math.sqrt(Math.pow(avgDist, 3) / GM);

Math.PI is equal to π (pi)
Math.sqrt(number) is used to calculate the square root of the inner result, Math.sqrt(4) = √4 = 2
Math.pow(base, exponent) takes two arguments, base and exponent. It will return the base to the exponent power, Math.pow(3, 2) = 3² = 9
```
```
orbitalPeriod([{name : "sputnik", avgAlt : 35873.5553}]) 
应该返回 [{name: "sputnik", orbitalPeriod: 86400}].

orbitalPeriod([{name: "iss", avgAlt: 413.6}, {name: "hubble", avgAlt: 556.7}, {name: "moon", avgAlt: 378632.553}]) 
应该返回 [{name : "iss", orbitalPeriod: 5557}, {name: "hubble", orbitalPeriod: 5734}, {name: "moon", orbitalPeriod: 2377399}].

```

Remember, that we must sum both, distance from the surface and radius of the planet to get the total distance from the planet’s core:
```javascript
function getOrbitalPeriod(avgAltitude, planetRadius, GM) {
  return 2 * Math.PI * Math.sqrt(Math.pow(avgAlt + planetRadius, 3) / GM);
}
```
We can round numbers in JavaScript using the following methods:

`Math.floor()`: Returns the largest integer less that or equal to the given number.
```javascript
Math.floor(6.1); //-> 6
Math.floor(6.7); //-> 6
```
`Math.ceil()`: Returns the lowest integer greater than or equal to the given number.
```javascript
Math.ceil(5.2); //-> 6
Math.ceil(5.7); //-> 6
```
`Math.round()`: Returns the value of the number rounded to the nearest integer.
```javascript
Math.round(5.3); //-> 5
Math.round(5.5); //-> 6
Math.round(5.7); //-> 6
```

It would seem that `Math.round()` could do the job, let’s round our result before we return it
```javascript
function getOrbitalPeriod(avgAltitude, planetRadius, GM) {
  return Math.round(2 * Math.PI * Math.sqrt(Math.pow(avgAltitude + planetRadius, 3) / GM));
}
```

Great! Now that we can easily compute the orbital period of any given object (we can even use it for different planets since we are using GM and radius as variables!) 
let’s apply this to an array of satellites. 
We are going to use the `Array.prototype.map()` method, which applies a function to every element inside an array, and returns the result. 

```javascript
function orbitalPeriod(array) {
  var GM = 398600.4418,
      earthRadius = 6367.4447;// These two are given to us!

  var result = array.map(function(currentElement) {
    return {
      name: currentElement.name,
      orbitalPeriod: getOrbitalPeriod(currentElement.avgAlt, GM, earthRadius)  // We get the orbital radius using the previous function!
    };
  });

  return result;

  function getOrbitalPeriod(avgAltitude, GM, planetRadius) {
    return Math.round(2 * Math.PI * Math.sqrt(Math.pow(avgAltitude + planetRadius, 3) / GM));
  }
}

orbitalPeriod([{name : "sputnik", avgAlt : 35873.5553}]);

```

EXTRA:

If you don’t feel to conformable using the map method, try using a forEach and push instead!
```javascript
function orbitalPeriod(arr) {
  var results = [];
  var GM = 398600.4418,
      earthRadius = 6367.4447;

  arr.forEach(function(element) {
    results.push({
      name: element.name,
      orbitalPeriod: getOrbitalPeriod(element.avgAlt, GM, earthRadius)
    });
  });

  return results;

  function getOrbitalPeriod(avgAlt, GM, planetRadius) {
    return Math.round(2 * Math.PI * Math.sqrt(Math.pow(avgAlt + planetRadius, 3) / GM));
  }
}
orbitalPeriod([{name : "sputnik", avgAlt : 35873.5553}]);

```