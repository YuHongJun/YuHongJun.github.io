---
author: Demi_YuHongJun
comments: true
date: 2017-04-26 09:42:32+00:00
layout: post
title:  Github提交不记录Contributions 
description:  Github提交不记录Contributions 
categories:
- Tech
tags:
- git
---
* 目录
{:toc}
---
写的代码提交到Github上时，contributions不记录当前提交记录。查了资料，发现原因。 

官方上面有解释: [Why are my contributions not showing up on my profile?](https://help.github.com/articles/why-are-my-contributions-not-showing-up-on-my-profile/)

记录下自己的解决步骤：
##### 使用Git log 查看当前commit log
```git
commit 7874b5147596e495c4d
Author: xxx <xxx@xxx.com>
Date:   Fri Apr 28 11:01:19 2017 +0800

    2017-4-28 add content

```
会看到log信息。确认Author是否和Github上的邮箱是否一致。如果不一致，那绝对就是这个问题了。
##### 用户名和邮箱地址的作用

用户名和邮箱地址是本地git客户端的一个变量

每次commit都会用用户名和邮箱纪录。

github的contributions统计就是按邮箱来统计的。

##### 配置一个全局的用户名和邮箱  [set-up-git](https://help.github.com/articles/set-up-git/)
```git
$ git config --global user.name "github's Name"

$ git config --global user.email "xxx@xxx.com"

$ git config --list
```

##### 如果你公司的项目是放在自建的Gitlab上面, 如果你不进行配置用户名和邮箱的话, 则会使用全局的, 这个时候是错误的, 正确的做法是针对公司的项目, 在项目根目录下进行单独配置
```git
$ git config user.name "gitlab's Name"

$ git config user.email "xxx@xx.com"

$ git config --list

 git config --list查看当前配置, 在当前项目下面查看的配置是全局配置+当前项目的配置, 使用的时候会优先使用当前项目的配置
```
*另外：分支commit,push不记录Contributions，默认只有master.*
#### 什么样的Contribution Github才记录？
翻译一下Github关于Contributions的说明，希望能帮到大家，不要让辛辛苦苦写的代码被Github忽视了:)

##### 会被记录的Contribution情形
1. Issues and pull requests

同时满足以下两个条件将会被计入Contribution
>这个操作是在一年之内。（Calendar只显示一年之内的Contribution）

>这个操作是针对一个独立的仓库。（在Fork的仓库中进行的操作不会被记录）

2. Commits

同时满足以下四个条件将会被计入Contribution

>Commits是在一年之内。（Calendar只显示一年之内的Contribution）

>进行Commits的用户被关联到了你的Github帐号中（使用SSH方式能够不输入帐号密码进行push，如果此时你Commit的帐号不在Github帐号列表中，就不会被计入Contribution）

>是在一个独立的版本库中进行Commit。（在Fork的仓库中进行Commit则不会被记录）

>是在这个版本库的默认分支（通常是Master）进行的Commit。（如果你在Dev分支下进行开发，你的Commit不会被计入Contribution，但是并不会丢失它们，一旦当你Merge到Master分支后，所有的Commit都会被重新计入。多人协作也是同理，只有被并入Master分支的Commit才会被计入，如果你的Commit在合并时被组长丢弃，在Github看来，你就白干了……）

3. 附加条件：如果你Commit的仓库不是你创建的，那么至少要满足以下四条之一，才会被计入Contribution

>你是这个仓库的协作者，或者是这个版本库的拥有组织中的一员。

>你fork过这个仓库。

>你对这个仓库发起过pull request或者issue。

>你对这个仓库标记了Star。
（私有仓库的Commit也会被计入Contribution，没有这个私有仓库权限的用户将看不到这个Commit的跳转链接）

##### Contributions未被Github计入的几个常见原因

1. 进行Commits的用户邮箱没有被关联到你的Github帐号中。
2. 不是在这个版本库的默认分支（master）进行的Commit。
3. 这个仓库是一个Fork仓库，而不是独立仓库。
 




