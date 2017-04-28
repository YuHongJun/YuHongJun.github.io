---
author: Demi_YuHongJun
comments: true
date: 2015-04-27 18:16:58+00:00
layout: post
slug: make-bootstrap-navbar-link-active-dynamically
title: 设置Bootstrap Navbar链接的动态Active效果/Make Bootstrap Navbar Link Active Dynamically
wordpress_id: 233
categories:
- Tech
tags:
- bootstrap
- javascript
- php
---

Actually I tried different Javascript function to do this, they are note good to solve the problem.

Normally you can used Javascript function below to solve the problem:

一般可以用以下的js function来增加和删除已有的class来解决这个问题：

```javascript
$(".nav a").on("click", function(){
   $(".nav").find(".active").removeClass("active");
   $(this).parent().addClass("active");
});
```

Unfortunately, I found that the JS I used may conflict with Bootstrap JS. I can only click the link but the page didn’t go to the new link address. In the end I used HTML within php function to switch class from last "<**li**>" to current "<**li**>".

可能是bootstrap的js跟我写的这个js功能有冲突，在我在使用时只有class的改变，链接高亮的部分切换到新的tab，但是页面并没有真的链接过去。所有我认为在bootsrap里面用php来进行操作可能更好，不会和现有的所有js功能相冲突。

- Call a php function inline within the markup passing in the links destination request url

markup passing in the links destination request url

```php

<ul class="nav">
    <li <?=echoActiveClassIfRequestMatches("home")?>>
        <a href="home.php">Search</a></li>
    <li <?=echoActiveClassIfRequestMatches("about")?>>
        <a href="about.php">About</a></li>
</ul>

```

### PHP function

The php function simple needs to compare the passed in request uri and if it matches the current page being rendered output active class.

```php
< ?php 
function echoActiveClassIfRequestMatches($requestUri)
{
    $current_file_name = basename($_SERVER['REQUEST_URI'], ".php");
 
    if ($current_file_name == $requestUri)
        echo 'class="active"';
}
?>
```

