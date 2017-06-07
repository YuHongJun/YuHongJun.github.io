---
author: Demi_YuHongJun
comments: true
date: 2017-06-06 18:42:32+00:00
layout: post
title: Exact Change(算法 高级)
description: Exact Change(算法 高级)
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---
https://www.freecodecamp.cn/challenges/exact-change

设计一个收银程序 `checkCashRegister()` ，其把购买价格(`price`)作为第一个参数 , 付款金额 (`cash`)作为第二个参数, 和收银机中零钱 (`cid`) 作为第三个参数.

cid 是一个二维数组，存着当前可用的找零.

当收银机中的钱不够找零时返回字符串 `"Insufficient Funds"`. 如果正好则返回字符串 `"Closed"`.

否则, 返回应找回的零钱列表,且由大到小存在二维数组中.

当你遇到困难的时候，记得查看错误提示、阅读文档、搜索、提问。

这是一些对你有帮助的资源:

[Global Object](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object)

思路：

1. we’ll just think in cents instead of dollars

2. Let’s use a simple switch statement and return the value for each type of coin in cents

3. Then, while the cash left is greater that the current coin/bill and we still have coins/bills of this type, we remove it’s value from the change left and remove a coin. We’ll keep track of how many coins of each type we’ve given back so we can create an array with the result. Let’s see the code and comment each line:

```javascript
function checkCashRegister(price, cash, cid) {
    cash = cash * 100;
    price = price * 100;

    var change = cash - price,
        changeLeft = change;

    var totalCid = getTotalCid(cid);
    var result =[];

    if (change > totalCid) {
        return 'Insufficient Funds';
    } else if (change === totalCid) {
        return 'Closed';
    }

 
    for (var i = cid.length - 1; i >= 0; i--) {     // We loop over the cash-in-drawer array in reverse order.
        var coinName = cid[i][0],                   // We set the coin name.
            coinTotal = cid[i][1] * 100,            // We set the total cash in that type of coin (times 100 for cents!).
            coinValue = getValue(coinName),         // We get the value of a single coin/bill using it's name.
            coinAmount = coinTotal / coinValue,     // We get the amount of coins of it's type by dividing the total cash by the value of a single unit.
            toReturn = 0;                           // Counter: How many coins of this type we are returning.
 
        while (changeLeft >= coinValue && coinAmount > 0) { // While change is greater that the value the current coin/bill:
            changeLeft -= coinValue;                        // Substract the value of a single coin/bill from the change left.                  
            coinAmount--;                                   // Remove one coin/bill since we are returning it.
            toReturn++;                                     // Add one to the counter.
        }
 
        // When the loop is done (because there is no coins/bills of the current
        // type left or the change left is less than the value of the current coin/bill)
        if (toReturn > 0) {
            // We push the coin and total to return in that type of coin/bill to the result.
            // We get this value by multiplying the value of a single coin/bill by it's value, and then divide by 100 to get the value in dollars.
            result.push([coinName, toReturn * coinValue / 100]);
        }
    }
 
    // Return something!

    // We make use of the getTotalCid method that we created earlier to see how much money we are actually returning.
    // If it's not equal to the original change, it means that we can't return that exact amount with the current cash-in-register.
    if (getTotalCid(result) !== change) {
        return 'Insufficient Funds';            // Return early.
    }

    return result;  // Everything went OK, we return the result!


    function getTotalCid(cid) {
        var total = 0;
        for (var i = 0; i < cid.length; i++) {
            total += cid[i][1] * 100;
        }
        return total;
    }

    function getValue(coinOrBill) {
        switch (coinOrBill) {
            case 'PENNY':
                return 1;
            case 'NICKEL':
                return 5;
            case 'DIME':
                return 10;
            case 'QUARTER':
                return 25;
            case 'ONE':
                return 100;
            case 'FIVE':
                return 500;
            case 'TEN':
                return 1000;
            case 'TWENTY':
                return 2000;
            case 'ONE HUNDRED':
                return 10000;
        }
    }
}

// Example cash-in-drawer array:
// [["PENNY", 1.01],
// ["NICKEL", 2.05],
// ["DIME", 3.10],
// ["QUARTER", 4.25],
// ["ONE", 90.00],
// ["FIVE", 55.00],
// ["TEN", 20.00],
// ["TWENTY", 60.00],
// ["ONE HUNDRED", 100.00]]

checkCashRegister(18.50, 20.00, [["PENNY", 1.01], ["NICKEL", 2.05], ["DIME", 3.10], ["QUARTER", 4.25], ["ONE", 90.00], ["FIVE", 55.00], ["TEN", 20.00], ["TWENTY", 60.00], ["ONE HUNDRED", 100.00]]);

```


[exact-change-free-code-camp](https://www.gorkahernandez.com/blog/exact-change-free-code-camp/)