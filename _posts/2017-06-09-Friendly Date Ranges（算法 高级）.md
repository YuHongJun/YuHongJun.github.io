---
author: Demi_YuHongJun
comments: true
date: 2017-06-09 04:42:32+00:00
layout: post
title: Friendly Date Ranges（算法 高级）
description: Friendly Date Ranges（算法 高级）
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---

https://www.freecodecamp.cn/challenges/friendly-date-ranges

让日期区间更友好！

把常见的日期格式如：YYYY-MM-DD 转换成一种更易读的格式。

易读格式应该是用月份名称代替月份数字，用序数词代替数字来表示天 (1st 代替 1).

记住不要显示那些可以被推测出来的信息: 如果一个日期区间里结束日期与开始日期相差小于一年，则结束日期就不用写年份了。月份开始和结束日期如果在同一个月，则结束日期月份就不用写了。

另外, 如果开始日期年份是当前年份，且结束日期与开始日期小于一年，则开始日期的年份也不用写。

例如:

`makeFriendlyDates(["2016-07-01", "2016-07-04"])` 应该返回 `["July 1st","4th"]`

`makeFriendlyDates(["2016-07-01", "2018-07-04"])` 应该返回 `["July 1st, 2016", "July 4th, 2018"]`.

当你遇到困难的时候，记得查看错误提示、阅读文档、搜索、提问。

这是一些对你有帮助的资源:

[String.split()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/split)

[String.substr()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/substr)

[parseInt()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/parseInt)


#### 思路

先考虑主要逻辑，这题要我们按要求格式化传入日期。按题意要求，我们来分步解答。

取得字符串形式的开始日期、结束日期，存入变量 temp 。
```
var temp = function(i){
    return arr[i].split("-");
  };
temp(i) （ i 的值为0、1，分别代表开始、结束日期）打印出来的格式是这样：

["2022", "09", "05"]
```
“用月份名称代替月份数字”。新建数组 months ，准备与取得的日期建立对应关系。
```
var months = ["January","February","March","April","May","June","July","August","September","October","November","December"];
建立输出格式的代表月份的函数 m() ：

var m = function(month){
    return months[parseInt(temp(month)[1])-1];
  };
```

数组的索引是从零开始的，输入的月份是从一开始的，为了保持对应，记得要减一哦。

“用序数词代替数字来表示天 (1st 代替 1)”。
```javascript
var dayArr = ['1st', '2nd', '3rd', '4th', '5th', '6th',
    '7th', '8th', '9th', '10th', '11th', '12th', '13th',
    '14th', '15th', '16th', '17th', '18th', '19th', '20th',
    '21st', '22nd', '23rd', '24th', '25th', '26th', '27th',
    '28th', '29th', '30th', '31st'];

  var d = function(day){
   return dayArr[Number(day)-1];
  };

```

用以上三个变量我们可以拼接出正常情况的返回值。
```
var output = function(i){
    return m(i) + " " + d(temp(i)[2]) + "," + " " + temp(i)[0];
  };
```

判断逻辑开始之前，先做点前期准备：
```
var result = [];            //将返回的数组，最后应包含开始、结束日期
var str0 = output(0);   //开始日期
var str1 = output(1);   //结束日期
```

比较两个日期相差天数可以这样表示：
```
var intervalDays = parseInt(Math.abs(new Date(temp(0)) - new Date(temp(1)))/1000/60/60/24) + 1;
```
好了，让我们再看看额外要求。

“如果一个日期区间里结束日期与开始日期相差不超一年，则结束日期就不用写年份了”。
```
if(intervalDays <= 365){
    str1 = str1.slice(0,output(1).indexOf(","));
  }
```

“月份开始和结束日期如果在同一个月，则结束日期月份就不用写了”。
```
if(intervalDays < 32 && m(0) === m(1)){
    str1 = str1.slice(output(1).indexOf(" ") + 1);
  }
```

“如果日期区间内开始日期年份是当前年份，且结束日期与开始不超过一年，则开始日期的年份也不用写”。
```
 //题目答案以2016年为当前年份。。。所以在此基础上now.getFullYear()-1=2017-1
  if(temp(0)[0] == now.getFullYear()-1 && intervalDays < 365){
    str0 = str0.slice(0,output(0).indexOf(","));
    str1 = str1.slice(0,output(1).indexOf(","));
  }
```
另外要考虑的一种情况是，如果开始日期和结束日期是同一天的话，只要返回一个日期就好了。

```
if(temp(0).toString() === temp(1).toString()){
    result.push(str0);
    return result;
  }
```

除此之外的情况：
```
result.push(str0,str1);
最后函数返回 result ，顺利解决！
```

#### 解法
```javascript
function makeFriendlyDates(arr) {
 var months =['January', 'February', 'March',
    'April', 'May', 'June', 'July', 'August', 'September',
    'October', 'November', 'December'];
var dayArr = ['1st', '2nd', '3rd', '4th', '5th', '6th',
    '7th', '8th', '9th', '10th', '11th', '12th', '13th',
    '14th', '15th', '16th', '17th', '18th', '19th', '20th',
    '21st', '22nd', '23rd', '24th', '25th', '26th', '27th',
    '28th', '29th', '30th', '31st'];
  var now = new Date();
  var result = [];
  var temp = function(i){
    return arr[i].split("-");
  };
  var m = function(month){
    return months[parseInt(temp(month)[1])-1];
  };

  var d = function(day){
   return dayArr[Number(day)-1];
  };

  var intervalDays = parseInt(Math.abs(new Date(temp(0)) - new Date(temp(1)))/1000/60/60/24) + 1;
  var output = function(i){
    return m(i) + " " + d(temp(i)[2]) + "," + " " + temp(i)[0];
  };
  var str0 = output(0);
  var str1 = output(1);
  if(intervalDays <= 365){
    str1 = str1.slice(0,output(1).indexOf(","));
  }
  if(intervalDays < 32 && m(0) === m(1)){
    str1 = str1.slice(output(1).indexOf(" ") + 1);
  }
  //题目答案以2016年为当前年份。。。所以在此基础上now.getFullYear()-1=2017-1
  if(temp(0)[0] == now.getFullYear()-1 && intervalDays < 365){
    str0 = str0.slice(0,output(0).indexOf(","));
    str1 = str1.slice(0,output(1).indexOf(","));
  }
  if(temp(0).toString() === temp(1).toString()){
    result.push(str0);
    return result;
  }
  result.push(str0,str1);
  return result;
}
makeFriendlyDates(["2017-03-21", "2017-05-05"]);

```