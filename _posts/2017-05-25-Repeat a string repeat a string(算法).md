---
author: Demi_YuHongJun
comments: true
date: 2017-05-25 09:42:32+00:00
layout: post
title: Repeat a string repeat a string(算法)
description: Repeat a string repeat a string(算法)
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---

https://www.freecodecamp.cn/challenges/repeat-a-string-repeat-a-string

#### 解法

#### 解法 一 （推荐效率高）

```javascript
   function repeat(pattern, count) {
     // repeat after me
     if (count < 1) return '';
       var result = '';
       while (count > 1) {
           if (count & 1) result += pattern;
           count >>= 1, pattern += pattern;
       }
       return result + pattern;
   }
   
   repeat("abc", 4);
   
   ```

#### 解法二  （效率也高）

http://www.webreference.com/programming/javascript/jkm3/3.html
```javascript
function repeat(x, n) {
  // repeat after me
    var s = ''; 
  if(n<1) return s;
    for (;;) { 
        if (n & 1) s += x; 
        n >>= 1; 
        if (n) x += x; 
        else break; 
    } 
    return s; 
}

repeat("abc", 4);

```

#### 解法 三
This answer is old and and not terribly practical - it's just "clever" because it uses Array stuff to get String things done. When I wrote "less process" I definitely meant "less code" because, as others have noted in subsequent answers, it performs like a pig. So don't use it if speed matters to you.

```javascript
function repeat(str, num) {
  // repeat after me
  if(num<1){
    return '';
  }else{
         return new Array( num + 1 ).join( str );
  }

}

repeat("abc", 3);

```

#### 解法四
```javascript
function repeat(str, num) {
  // repeat after me
  if ( num < 1) {
    return "";
  }else {
    return str.repeat(num);
  }

}

repeat("abc", 3);

```





