---
author: Demi_YuHongJun
comments: true
date: 2016-08-06 09:42:32+00:00
layout: post
title: 实现 select中指定option选中触发事件
description: 实现 select中指定option选中触发事件
keywords: javascript
categories:
- Tech
tags:
- javascript
---
* 目录
{:toc}
---

我们在用到下拉列表框select时，需要对选中的<option>选项触发事件，其实<option>本身没有触发事件方法，我们只有在select里的onchange方法里触发。

虽然我曾经处理过类似的问题,用过就忘是不是猪脑子....

记录下

当我们触发select的双击事件时，用ondblclick方法。
当我们要取得select的选中事件时，用`document.all['name'].value`来获取，其中name是select的名称。
如果我们要得到select的全部的值就用一个for循环来实现。代码如下：
```javascript
var vi = document.all['list'].length;
for(var i=0;i<vi;i++){
document.form2.list(i).value; //form2是<form>的名称
}
```

```
‍‍<select id="pid" onchange="gradeChange()">

    <option grade="1" value="a">选项一</a>

    <option grade="2" value="b">选项二</a>

</select>

<script type="text/JavaScript">
       function gradeChange(){
        var objS = document.getElementById("pid");
        var grade = objS.options[objS.selectedIndex].grade;
        alert(grade);
       }
</script>
```


```
<select name="myselect" id="myselect">
    <option value="opt1">选项1</option>
    <option value="opt2">选项2</option>
    <option value="opt3">选项3</option>
</select>
 
$("#myselect").change(function(){
    var opt=$("#myselect").val();
    ...
});
```

