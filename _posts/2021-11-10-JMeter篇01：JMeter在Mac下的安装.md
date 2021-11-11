---
author: Demi_YuHongJun
comments: true
date: 2021-11-10 05:42:32+00:00
layout: post
title: JMeter篇01：JMeter在Mac下的安装
description: JMeter篇01：JMeter在Mac下的安装
keywords: JMeter
categories:
- Tech
tags:
- JMeter
- Mac
---
* 目录
{:toc}
---

## JMeter篇01：JMeter在Mac下的安装
> 其实不论操作系统是Windows、Unix（如Mac OS）、Linux（如Ubuntu）等，JMeter所需要的基础环境配置都是类似的，本文介绍JMeter for MAC的安装与环境配置。

### JMeter安装步骤如下：
#### 安装JDK
##### 选择版本

Java 8，[下载地址](https://www.oracle.com/java/technologies/downloads/#java8)，[历史版本下载地址](https://www.oracle.com/java/technologies/downloads/)

JMeter 5.0，[下载地址](http://jmeter.apache.org/download_jmeter.cgi)，[历史版本下载地址](https://archive.apache.org/dist/jmeter/binaries/)

##### 安装JDK

> 如果你在终端（Terminal）输入java -version，可以得到JDK的版本，并且是Java 8以上，那就可以跳过这一步。

进入Java 8的下载地址页面，选择适用于Mac OS的JDK版本，点击下载。

下载完后，打开文件，进入安装页面。

安装过程非常简单，按“继续”按钮一直下一步即可。

安装完成后，打开终端（Terminal），输入以下命令可用于检查本机是否安装了JDK：
```
  java -version # 检查JDK版本
  /usr/libexec/java_home -V # 列出所有JDK版本的JAVA_HOME
```

##### 配置Java环境变量

如果你已经配置好了环境变量，在终端（Terminal）输入echo $JAVA_HOME，echo $PATH，echo $CLASSPATH，里面包含正确的JDK路径，那就可以跳过这一步。

JDK安装成功后，需要配置环境变量，在Windows下需要配置的环境变量是"JAVA_HOME”、"path”、"classpath"，Mac下也是类似。

JAVA_HOME：指向JDK的安装目录；
path：指定命令搜索路径，设置好path变量后，就可以在任何目录下执行javac/java等工具了；
classpath：指定类搜索路径；
打开终端，输入vim .bash_profile，会进入vim编辑器，如下图：


在.bash_profile文件中进行环境变量的配置，输入以下代码（#后面的是注释，为了方便我解释，不需要输入）。
```
export JAVA_8_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_181.jdk/Contents/Home # 等号右边的路径目录，可以通过/usr/libexec/java_home -V这个命令得到
export JAVA_HOME=$JAVA_8_HOME # 设置一个中间变量，为了方便多个JDK版本时更换JAVA_HOME
export PATH=$JAVA_HOME/bin:$PATH:. #冒号前代表JDK目录下的bin目录，冒号后代表当前目录
export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
```
>vim编辑器的使用有点特别，有意思的是，“程序员一旦进入Vim，就再难以脱身”。Stack Overflow上关于怎样退出Vim的问题，其点击量已有上百万次了。
对于vim的基础使用，可以参考这篇[菜鸟教程](https://www.runoob.com/linux/linux-vim.html)。

环境变量就配置好了，分别输入esc（退出输入模式Insert Mode）、冒号（切换到底线命令模式Last line mode）、w（保存文件）、q（退出文件）、回车（执行命令），即可退出vim编辑器，并保存.bash_profile文件。

继续在终端中输入source ~/.bash_profile，作用是让这个配置文件在修改后立即生效，最后，输入echo $JAVA_HOME，当输出的JAVA_PATH正确时，证明环境变量已经配置成功了。


##### 安装JMeter
进入JMeter的下载地址页面，如下图，有两个版本可供下载：

Binaries：二进制版，即已经编译好、可直接执行；
Source：源代码版，需要自己编译；

我们下载apache-jmeter-5.4.1.tgz这个Binaries版本，下载完成后，解压，可以通过Finder（访达）页面双击这个文件解压，也可以通过终端输入tar zxvf apache-jmeter-5.0.tgz解压。

##### 启动JMeter
解压完成后，得到下面的目录文件：

进入到bin目录下，通过sh jmeter命令来启动JMeter，如下图


Don't use GUI mode for load testing：这是一段提示信息，不要使用GUI模式进行负载测试，要使用NON GUI模式

实际上，只要配置好Java的环境变量，下载JMeter，即可启动。

##### 进一步优化
现在，我们已经可以成功启动JMeter了，但是每次都需要打开终端、进入到JMeter的bin目录下，输入sh jmeter命令来启动，显得有点繁琐。

当我们对~/.bash_profile这个文件熟悉后，可以直接把JMeter配置到环境变量中。

还是通过vim .bash_profile进入到vim编辑器，输入以下命令：
```
export JMETER_HOME=/Users/stefan/MyProjects/apache-jmeter-5.0
export PATH=$JAVA_HOME/bin:$PATH:.:$JMETER_HOME/bin:$PATH
export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:$JMETER_HOME/lib/ext/ApacheJMeter_core.jar:$JMETER_HOME/lib/jorphan.jar:$JMETER_HOME/lib/logkit-2.0.jar
```

退出vim编辑器，输入source ~/.bash_profile。接下来重点来了，直接在终端（任意目录）输入jmeter，即可启动JMeter。

##### 更改JMeter语言为中文
启动JMeter的GUI模式后，默认语言是英文，它也自带了几种语言，我们可以把JMeter切换成中文，从菜单栏中进行切换，方法如下图。Chinese（Simplified）的意思是中文（简体），Chinese（Traditional）的意思是中文（繁体）。

设置完成后，关闭JMeter，重新启动GUI模式，会发现，语言又变成英文了。所以如果要更改默认语言为中文，需要修改配置文件，即MyProjects/apache-jmeter-5.4.1/bin/jmeter.properties这个文件。

用Sublime Text或者其他的文本编辑器打开这个文件，找到这块区域：
```
#Preferred GUI language. Comment out to use the JVM default locale's language.
#language=en
修改为：

#Preferred GUI language. Comment out to use the JVM default locale's language.
language=zh_CN
```
再次打开JMeter后，会发现默认语言变为中文。

##### 小结
本篇文章主要讲了JMeter的安装、环境变量的配置、使用Tips等。实际上，JMeter本身的安装很简单，只是Java的环境变量配置比较繁琐，对于没有开发经历的测试人员来说，可能摸不到头脑。
