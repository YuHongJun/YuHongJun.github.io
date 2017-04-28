---
author: Demi_YuHongJun
comments: true
date: 2015-06-02 19:45:42+00:00
layout: post
title: Javascript Include Html Page By Jquery
categories:
- Tech
tags:
- javascript
- Html5
---
如果页面不用php编程，而且想用javascript来像php一样include页面的话，可以用jquery的load function来实现，代码如下：

```
    <html> 
      <head> 
        <script src="jquery.js"></script> 
        <script> 
        $(function(){
          $("#includedContent").load("b.html"); 
        });
        </script> 
      </head> 
    
      <body> 
         <div id="includedContent"></div>
      </body> 
    </html>
```


b.html:

```
     This is my include file 
```




附上Jquey官网的说明：[http://api.jquery.com/load/](http://api.jquery.com/load/)
