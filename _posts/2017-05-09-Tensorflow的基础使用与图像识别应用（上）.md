---
author: Demi_YuHongJun
comments: true
date: 2017-05-09 09:42:32+00:00
layout: post
title: 【转】Tensorflow的基础使用与图像识别应用（上）
description: Tensorflow的基础使用与图像识别应用（上）
keywords: Tensorflow, Machine Learning
categories:
- Tech
tags:
- Tensorflow
---
* 目录
{:toc}
---

Tensorflow的基础使用与图像识别应用分享会笔记总结：

大家好， 非常高兴大家今晚能参加 Tensorflow 的公开课， 我是本次公开课的主讲人覃秉丰。今晚的公开课会分成两个部分， 第一部分会介绍 Tensorflow 的基础使用， 第二部分会给出具体代码来给大家讲解如何用 Tensorflow 来做图像识别。下面我们开始今天的内容。

![t1](https://yuhongjun.github.io/assets/media/05-2017/t1.png)


Tensorflow 是 google 第二代人工智能学习系统。支持 python 和 c++语言， 支持 CNN、 RNN 和 LSTM 等算法， 可以被用于语音识别或图像处理等多项深度学习领域。它可以在一个或多个 CPU 或 GPU 中运行。它可以运行在嵌入式系统(如手机， 平板电脑)中， PC 中以及分布式系统中。它是目前全世界最火爆的深度学习平台(没有之一)。

深度学习这个行业刚刚兴起， 急需一个好的平台来提高我们的工作效率。 google 在 2015 年 12 月 11 日开源了 Tensorflow， google 希望把Tensorflow 做成行业标准。我个人也是比较看好 Tensorflow， 毕竟Google 的技术水平和公司实力都是全世界数一数二的。我们学习了Tensorflow 之后， 就可以使用 Tensorflow 非常方便地搭建一些我们自己的深度网络， 实现我们想要的一些功能。

下面我们通过 Tensorboard 来展示一下 Tensorflow。 Tensorboard 是一个与 Tensorflow 配套的可视化的调试工具。

![t2](https://yuhongjun.github.io/assets/media/05-2017/t2.png)


这是 Tensorboard 中保存的模型运行过程中保存下来的训练数据集和测试数据集的准确率变化曲线。其中紫色的曲线是训练数据集的accuracy 曲线， 蓝色的曲线是测试数据集的 accuracy 曲线。从图中我们能观察到的信息有 accuracy 的数值， 训练的次数（ 图中一共训练了5000 次， 鼠标停在第 3250 次）， 训练的时间以及训练消耗了多少时间。

![t3](https://yuhongjun.github.io/assets/media/05-2017/t3.png)

Tensorboard 还能查看网络的结构， 以及各个结构之间的连接关系。通过网络的结构我们可以仔细地追踪数据(在 Tensorflow 中数据的基本格式是 Tensor)的流动。

![t4](https://yuhongjun.github.io/assets/media/05-2017/t4.png)

![t6](https://yuhongjun.github.io/assets/media/05-2017/t6.png)

![t7](https://yuhongjun.github.io/assets/media/05-2017/t7.png)
