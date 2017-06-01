---
author: Demi_YuHongJun
comments: true
date: 2017-05-29 09:42:32+00:00
layout: post
title: Caesars Cipher(算法 初级）
description: Caesars Cipher(算法 初级）
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---
https://www.freecodecamp.cn/challenges/caesars-cipher

让上帝的归上帝，凯撒的归凯撒。

下面我们来介绍风靡全球的凯撒密码Caesar cipher，又叫移位密码。

移位密码也就是密码中的字母会按照指定的数量来做移位。

一个常见的案例就是[ROT13](http://www.baike.com/wiki/ROT13&prd=so_1_doc)密码，字母会移位13个位置。由'A' ↔ 'N', 'B' ↔ 'O'，以此类推。

写一个[ROT13](http://www.baike.com/wiki/ROT13&prd=so_1_doc)函数，实现输入加密字符串，输出解密字符串。

所有的字母都是大写，不要转化任何非字母形式的字符(例如：空格，标点符号)，遇到这些特殊字符，跳过它们。

当你完成不了挑战的时候，记得开大招'Read-Search-Ask'。

这是一些对你有帮助的资源:

[String.charCodeAt()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/charCodeAt)

[String.fromCharCode()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/fromCharCode)

在JavaScript中可以通过 `String.charCodeAt()` 方法返回0至65535这间的整数，代表索引处理字符的UTF-16编码单元。 可以通过这个方法查出每个字符对应的ASCII编码：
```
'a' .charCodeAt();     //97 
'A' .charCodeAt();     //65 
'abc' .charCodeAt( 0 ); //97 
'ABC' .charCodeAt( 0 ); //65
```
Note: the lower-case 'a' is equal to 97, 'z' -> 122, 'A' -> 65, 'Z' -> 90.

解法一:
```javascript
function rot13(str) { // LBH QVQ VG!
    var index = null;
  var temp = "";
  var _A = "A".charCodeAt(0);
  var _Z = "Z".charCodeAt(0);
  var mid = (_A + _Z)/2;
  for(var i = 0; i < str.length; i++){
    index = str.charCodeAt(i);
    if(index >= _A && index <= mid ){
      temp += String.fromCharCode(index + 13);
    }else if(index <= _Z && index > mid ){
      temp += String.fromCharCode(index - 13);
    }else{
      temp += String.fromCharCode(index);
    }   
  }
  return temp;

}

// Change the inputs below to test
rot13("SERR PBQR PNZC");

```
解法二:
```
function rot13(str) { // LBH QVQ VG!
 var newString = [];     // charCodeAt()返回0-65535之间的整数   
  for ( var i = 0 ; i < str.length; i++) {        
    var temp = str.charCodeAt(i);// 如果字符是非大写英文字母(序号小于65或大于91)，将该字符直接放到newString中，并使用continue进入下一个循环        
      if (temp < 65 || temp > 91 ) { // 返回字符串指定位置的字符           
    newString.push(str.charAt(i));            
        continue ; // 如果序号大于77(N-Z字母)，使用String.fromCharCode()转找成该序号减13的字符，并且放入newString       
      } else if (temp > 77 ) {  // String.fromCharCode()根据序号(指定的Unicode编码中的序号)值来返回一个字符串            
        newString.push(String.fromCharCode(temp - 13 ));  // 如果序号小于78(N-Z字母)，使用String.fromCharCode()转找成该序号减13的字符，并且放入newString      
      } else {            newString.push(String.fromCharCode(temp + 13 ));      
             }   
  }    
  return newString.join( "" );
}

// Change the inputs below to test
rot13("serr PBQR PNZC");

```