---
author: Demi_YuHongJun
comments: true
date: 2015-04-15 23:27:31+00:00
layout: post
title: 一个表单多个按钮提交到不同Action/Different Buttons to submit One Form To different Url
wordpress_id: 223
categories:
- Tech
tags:
- javascript
- php
---

简单的来说，就是你有一个表，但是有多个按键需要将同一个表submit到不同的地址去。

这个问题有若干个解决办法，最简单直接的方法我在这边使用的是用Javascript的function去将不同的Button的function链接到不同的Link。

```

<script language="Javascript">
  
    function   goAction(url)   {  
      formname.action=url;//formname为当前form的name 多个form时 在此处获取form即可  
      formname.submit();//submit form
}  
</script>

<form action=" " method="post " name="formname">
<button type="button " name="ToA " value="ToA " onclick="goAction('A.php');">A</button>
<button type="button " name="ToB " value="ToB " onclick="goAction('B.php');">B</button>
<button type="button " name="ToC " value="ToC " onclick="goAction('C.php');">C</button>
</form>;

``` 
