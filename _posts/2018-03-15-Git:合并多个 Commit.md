---
author: Demi_YuHongJun
comments: true
date: 2018-03-15 05:42:32+00:00
layout: post
title: 2018-03-15-Git:合并多个 Commit
description: 2018-03-15-Git:合并多个 Commit
keywords: Deploy
categories:
- Tech
tags:
- Git
---
* 目录
{:toc}
---

2018-03-15-Git:合并多个 Commit

```
git rebase -i branch-name
pick 的意思是要会执行这个 commit
squash 的意思是这个 commit 会被合并到前一个commit
输入wq保存并推出
会看到 commit message 的编辑界面
再次输入wq保存并推出, 输入git log查看 commit 历史信息，你会发现这两个 commit 已经合并了。
注意事项：如果这个过程中有操作错误，可以使用 git rebase --abort来撤销修改，回到没有开始操作合并之前的状态。
```


