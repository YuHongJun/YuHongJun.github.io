---
author: Demi_YuHongJun
comments: true
date: 2021-06-12 05:42:32+00:00
layout: post
title: Go语言Sprintf
description: Go语言Sprintf
keywords: Go
categories:
- Tech
tags:
- Go
- Go
---
* 目录
{:toc}
---

## Go语言Sprintf

fmt.Sprintf（格式化输出）
Go语言fmt.Sprintf（格式化输出）
 

fmt.Sprintf(格式化样式, 参数列表…)

格式化样式：字符串形式，格式化动词以%开头。
参数列表：多个参数以逗号分隔，个数必须与格式化样式中的个数一一对应，否则运行时会报错。

在 Go 语言中，格式化的命名延续C语言风格：
```
var progress = 2
var target = 8
```
// 两参数格式化
```
title := fmt.Sprintf("已采集%d个药草, 还需要%d个完成任务", progress, target)
fmt.Println(title)
pi := 3.14159
```
// 按数值本身的格式输出
```
variant := fmt.Sprintf("%v %v %v", "月球基地", pi, true)
fmt.Println(variant)
```
// 匿名结构体声明, 并赋予初值
```
profile := &struct {
Name string
HP int
}{
Name: "rat",
HP: 150,
}
fmt.Printf("使用'%%+v' %+v\n", profile)
fmt.Printf("使用'%%#v' %#v\n", profile)
fmt.Printf("使用'%%T' %T\n", profile)
var progress = 2
var target = 8
```
// 两参数格式化
```
title := fmt.Sprintf("已采集%d个药草, 还需要%d个完成任务", progress, target)

fmt.Println(title)

pi := 3.14159
```
// 按数值本身的格式输出
```
variant := fmt.Sprintf("%v %v %v", "月球基地", pi, true)

fmt.Println(variant)

// 匿名结构体声明, 并赋予初值
profile := &struct {
    Name string
    HP   int
}{
    Name: "rat",
    HP:   150,
}

fmt.Printf("使用'%%+v' %+v\n", profile)

fmt.Printf("使用'%%#v' %#v\n", profile)

fmt.Printf("使用'%%T' %T\n", profile)
```
代码输出如下：
```
已采集2个药草, 还需要8个完成任务
"月球基地" 3.14159 true
使用'%+v' &{Name:rat HP:150}
使用'%#v' &struct { Name string; HP int }{Name:"rat", HP:150}
使用'%T' *struct { Name string; HP int }C语言中, 使用%d代表整型参数
```

下表中标出了常用的一些格式化样式中的动词及功能。
```
表：字符串格式化时常用动词及功能
动  词	功  能
%v	按值的本来值输出
%+v	在 %v 基础上，对结构体字段名和值进行展开
%#v	输出 Go 语言语法格式的值
%T	输出 Go 语言语法格式的类型和值
%%	输出 % 本体
%b	整型以二进制方式显示
%o	整型以八进制方式显示
%d	整型以十进制方式显示
%x	整型以十六进制方式显示
%X	整型以十六进制、字母大写方式显示
%U	Unicode 字符
%f	浮点数
%p	指针，十六进制方式显示
```