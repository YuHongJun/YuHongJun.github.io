---
author: Demi_YuHongJun
comments: true
date: 2017-06-07 04:42:32+00:00
layout: post
title: Inventory Update（算法 中级）
description: Inventory Update（算法 中级）
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---

https://www.freecodecamp.cn/challenges/inventory-update

依照一个存着新进货物的二维数组，更新存着现有库存(在 arr1 中)的二维数组. 如果货物已存在则更新数量 . 如果没有对应货物则把其加入到数组中，更新最新的数量. 返回当前的库存数组，且按货物名称的字母顺序排列.

当你遇到困难的时候，记得查看错误提示、阅读文档、搜索、提问。

这是一些对你有帮助的资源:

[Global Array Object](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array)

思路:

分析题意，现有库存 arr1 和新进货物 arr2 都是二维数组，每一项又能拆分为 value 、 key 两种。我们要把 arr2 中的 key 与 arr1 中的 key 进行比较，如果相同，则把 arr1 中相应的 value 值加上新进货物进行更新，如果 arr1 中的 key 没有相同值，说明该项是新品种货物，需要把整项加入 arr1 数组进行更新。

当现有库存 arr1 为空时，新进货物将全部更新为库存：
```javascript
if(arr1.length === 0){
    arr1 = arr2;
  }
```

将 arr1 中每一项与 arr2 逐条对比：
```javascript
arr1.forEach(function(item,index,array){
      for(var i = 0; i < arr2.length; i++){
         //do something...     
         }
    });
```
当 arr1 中已存在相同货物时：
```javascript
if(item[1] == arr2[i][1]){
            item[0] += arr2[i][0];
            break;
          }
```

arr1 中尚未有该货物：
```javascript
if(array.join().indexOf(arr2[i][1]) < 0){
            array.push(arr2[i]);
          }
```

循环外部对得到的 arr1 数组按 key 进行升序排序：
```javascript
arr1.sort(function(a,b){
    return a[1] > b[1];
  });
```

解法一:

```javascript
function updateInventory(arr1, arr2) {
    // All inventory must be accounted for or you're fired!
    if(arr1.length === 0){
    arr1 = arr2;
  }
  else{
    arr1.forEach(function(item,index,array){
      for(var i = 0; i < arr2.length; i++){
        //货物已存在
        if(item[1] == arr2[i][1]){
           item[0] += arr2[i][0];
           break;
        }
        //无对应货物
        if(array.join().indexOf(arr2[i][1]) < 0){
           array.push(arr2[i]);
        }    
      }
    });
  }
  arr1.sort(function(a,b){
    return a[1] > b[1];
  });
  return arr1;
}

// Example inventory lists
var curInv = [
    [21, "Bowling Ball"],
    [2, "Dirty Sock"],
    [1, "Hair Pin"],
    [5, "Microphone"]
];

var newInv = [
    [2, "Hair Pin"],
    [3, "Half-Eaten Apple"],
    [67, "Bowling Ball"],
    [7, "Toothpaste"]
];

updateInventory(curInv, newInv);

```


解法二：

```javascript
function updateInventory(arr1, arr2) {
    // All inventory must be accounted for or you're fired!
      if(arr1.length>0){
           arr2.forEach(function(vl,ix){
            var index=isExit(vl[1],arr1);
            if(index!==undefined){
              arr1[index][0]=arr1[index][0]+vl[0];
            }else{
              arr1.push(vl);
           }
         });
      }else{
        arr1=arr2;
      }
     //检查str是否在arr中存在,如果存在，返回下标
     function isExit(str,arr){
       for(var i=0;i<arr.length;i++)
         if(arr[i][1]==str) return i;      
     }
     return arr1.sort(function(a,b){
       return (a[1][0]>b[1][0])? 1 : 0;
     });
}

// Example inventory lists
var curInv = [
    [21, "Bowling Ball"],
    [2, "Dirty Sock"],
    [1, "Hair Pin"],
    [5, "Microphone"]
];

var newInv = [
    [2, "Hair Pin"],
    [3, "Half-Eaten Apple"],
    [67, "Bowling Ball"],
    [7, "Toothpaste"]
];

updateInventory(curInv, newInv);

```


结果：

updateInventory() 应该返回一个数组.

updateInventory([[21, "Bowling Ball"], [2, "Dirty Sock"], [1, "Hair Pin"], [5, "Microphone"]], [[2, "Hair Pin"], [3, "Half-Eaten Apple"], [67, "Bowling Ball"], [7, "Toothpaste"]]).length 应该返回一个长度为6的数组.

updateInventory([[21, "Bowling Ball"], [2, "Dirty Sock"], [1, "Hair Pin"], [5, "Microphone"]], [[2, "Hair Pin"], [3, "Half-Eaten Apple"], [67, "Bowling Ball"], [7, "Toothpaste"]]) 应该返回 [[88, "Bowling Ball"], [2, "Dirty Sock"], [3, "Hair Pin"], [3, "Half-Eaten Apple"], [5, "Microphone"], [7, "Toothpaste"]].

updateInventory([[21, "Bowling Ball"], [2, "Dirty Sock"], [1, "Hair Pin"], [5, "Microphone"]], []) 应该返回 [[21, "Bowling Ball"], [2, "Dirty Sock"], [1, "Hair Pin"], [5, "Microphone"]].

updateInventory([], [[2, "Hair Pin"], [3, "Half-Eaten Apple"], [67, "Bowling Ball"], [7, "Toothpaste"]]) 应该返回 [[67, "Bowling Ball"], [2, "Hair Pin"], [3, "Half-Eaten Apple"], [7, "Toothpaste"]].

updateInventory([[0, "Bowling Ball"], [0, "Dirty Sock"], [0, "Hair Pin"], [0, "Microphone"]], [[1, "Hair Pin"], [1, "Half-Eaten Apple"], [1, "Bowling Ball"], [1, "Toothpaste"]]) 应该返回 [[1, "Bowling Ball"], [0, "Dirty Sock"], [1, "Hair Pin"], [1, "Half-Eaten Apple"], [0, "Microphone"], [1, "Toothpaste"]].