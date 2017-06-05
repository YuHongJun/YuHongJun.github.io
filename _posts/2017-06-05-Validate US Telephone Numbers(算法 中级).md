---
author: Demi_YuHongJun
comments: true
date: 2017-06-05 15:42:32+00:00
layout: post
title: Validate US Telephone Numbers(算法 中级)
description: Validate US Telephone Numbers(算法 中级)
keywords: FreeCodeCamp
categories:
- Tech
tags:
- FreeCodeCamp
---
* 目录
{:toc}
---

https://www.freecodecamp.cn/challenges/validate-us-telephone-numbers

如果传入字符串是一个有效的美国电话号码，则返回 true.

用户可以在表单中填入一个任意有效美国电话号码. 下面是一些有效号码的例子(还有下面测试时用到的一些变体写法):
```
555-555-5555

(555)555-5555

(555) 555-5555

555 555 5555

5555555555

1 555 555 5555
```

在本节中你会看见如 `800-692-7753` or `8oo-six427676;laskdjf`这样的字符串. 你的任务就是验证前面给出的字符串是否是有效的美国电话号码. 区号是必须有的. 如果字符串中给出了国家代码, 你必须验证其是 `1`. 如果号码有效就返回 `true` ; 否则返回 `false`.

当你遇到困难的时候，记得查看错误提示、阅读文档、搜索、提问。

这是一些对你有帮助的资源:

[RegExp](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp)

```javascript
function telephoneCheck(str) {
  // Good luck!
  var phone = /^1? ?(\d{3}|\(\d{3}\))[ -]?\d{3}[ -]?\d{4}$/;
    return phone.test(str);

}

telephoneCheck("1 (555) 555-5555");
```

[validate-us-telephone-numbers-free-code-camp](https://www.gorkahernandez.com/blog/validate-us-telephone-numbers-free-code-camp/)