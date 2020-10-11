---
author: Demi_YuHongJun
comments: true
date: 2020-10-03 05:42:32+00:00
layout: post
title: Google Test
description: Google  Test
keywords: Deploy
categories:
- Tech
tags:
- Git
---
* 目录
{:toc}
---

https://mars.jetdevs.com/

Google Hacking的含义原指利用Google Google搜索引擎搜索信息来进行入侵的技术和行为；

https://venus.jetdevs.com/
```
现指利用各种搜索引擎搜索信息来进行入侵的技术和行为，但我们也可以利用这个在互联网上更加便捷精准的搜索我们想要的资源。

搜索参数介绍：

一、site，指定搜索的某個網站。例：desire site:bbs.gfan.com
二、filetype，指定搜索的文件類型。例：seo filetype:doc
三、双引号，代表完全匹配，使关键词不分开，顺序都不能变。
四、减号，事搜索结果更准确。减号与前一个关键词之间一定要有一个空格，与后一个关键词之间一定不能有空格。搜索结果为，匹配前一个关键词但不匹配后一个关键词的结果。例如：seo -搜索引擎。
五、AND，逻辑与，这个命令我们其实一直都在用，只是没有意识到。一般用空格代替，还可以用“+”代替。例如：霹雳布袋+败亡之剑，返回的结果同时包含两者。
六、intitle，在结果的标题中包含关键词，一次只能搜索一个关键词。
七、inurl，返回的结果的url中包含关键词。例如：seo inurl:byr，它将返回网址中包含byr，而内容中包含搜索词的结果。一次只能搜索一个关键词。
八、allintitle，在结果的标题中同时包含多个关键词。例如：allintitle:seo 搜索引擎，起作用相当于intitle:seo intitle:搜索引擎。allintitle属于排他性指令，不能与其他指令结合使用。
九、allinurl，结果的url中包含多个关键词。例如：allinurl:byr jobs，等于inurl:byr inurl:jobs。allinurl也是排他性指令
十、define，查询关键词的词义，起的是字典的作用。Google会返回包含查询关键词定义的网页，例如：define:computer ，支持汉字哦！
十一、xx in yy，单位换算，xx和yy代表需要换算的单位，且xx和yy为单位的英文缩写。例如你想知道一盎司等于多少千克，只需输入：1 oz in kg。
十二、weather，查询某一地区或城市的天气。不过我们这一地区或城市必须是Google能识别的，例如：weather:beijing，Google将会给我们返回北京的天气。
十三、intext，在结果的正文内容中包含关键词。例如：intext:剑圣，所有返回的网页正文中都包含“剑圣”。
十四、allintext，在结果的正文内容中同时包含多个关键词。排他性指令。
十五、星号（*），通配符，可以匹配任意字符串。例如：搜索*擎，则返回的结果中不仅有“搜索引擎”，还有“搜索巨擎”之类的。
十六、“.."，表示数值范围。例如：手机 2000..3000 元，注意“3000”与“元”之间必须有空格。另外，也可以是三个点。
十七、OR，逻辑或，可以用“|”代替。例如：霹雳布袋|败亡之剑，则返回的结果中，要么只含有“霹雳布袋”，要么就只含有“败亡之剑”，不可能是同时包含两个关键词的网页。
十八、info，查询网站的一些信息。例如：info:bbs.byr.cn，它只会返回一个结果，是一个选择列表，列表的选项是这个网站的某一方面的信息。info=cache+related+link+site+intext+intitle。
十九、related，查询与所给的网站类似的网站，它会返回Google认为的可能和你提供的网站类似的其他网站。例如：related:bbs.gfan.com，会返回安卓巴士，eoe社区，91等站点，但不会返回机锋网。其实这个命令Google经常在用，比如我们搜一个东西，Google除了返回给我结果，还会在结果下面给我们返回一些相关的词条。
二十、link，查询链接到这个url的页面。例如：link:bbs.gfan.com，会返回机锋网的所有外部链接。从其他页面指向机锋。
二十一、linkdomain，查询这个url链接的页面。例如：linkdomain:bbs.gfan.com -site:bbs.gfan.com，这样的结果比较准确，因为扫除了本身的干扰，它将返回机锋网链接到的页面。从机锋指向其他页面。
二十二、cache，提交cache:url，Google会显示当前网页的快照信息，从而替换网页的当前信息。这个命令现在也被Google集成到了搜索结果里，当你把鼠标悬浮在搜索结果上时，右侧会自动出现此结果的快照信息。
二十三、计算器功能。输入数学表达式，然后Google返回给你一个计算结果。强大的Google不仅支持普通运算，它还支持像三角函数、指数函数甚至是对数函数这样的高级运算。关键是，你会输入这些高级数学符号。
**下面是三个不怎么懂的命令，很少用，而且在有限的实践中也没弄明白是怎么回事，抄一段网上的解释在这里。***
二十四、inanchor，它返回的结果是导入链接锚文字中包含搜索词的页面。比如在Google搜索：inanchor:点击这里，返回的结果页面本身并不一定包含“点击这里”这四个字，而是指向这些页面的链接锚文字中出现了“点击这里”这四个字。需要注意区别与inurl，inurl是网页本身的url地址，而inanchor是在外部用于指向该url地址的文本（<a>..</a>之间文本）中找。例如：inanchor:download，你可能会发现有“FlashGet最佳的下载管理模式”，而该页面中根本就没有“download”字样。
二十五、allinanchor，inanchor的排他性指令。

二十六、daterange，当我们使用daterange进行查询的时候，Google会将查询的结果限制在一个特定的时间段内，这个时间相对于网站来说，是按网站被Google收录的时间算的。例如：”Spice Girls“ daterange:2450958-2450968。这里时间日期的格式是按天文学的儒略日。（这个搜索语法Google并不推荐使用，因为它会返回一些莫名其妙的东西）

 

allintext: = 搜索文本,但不包括网页标题和链接allinlinks: = 搜索链接, 不包括文本和标题WordA OR WordB = 搜索包含两关键词之一的页面“Word” OR “Phrase” = 精确的要求搜索单词或者句子WordA -WordB = 包含单词A但是不包含单词BWordA +WordB = 都包含~WORD = 寻找此单词和它的同义词~WORD-WORD = 只搜索同义词,不要原词

```
此语法在各大搜索引擎都是一样的，大家下去以后可以自行的测试

```
intext:
这个就是把网页中的正文内容中的某个字符做为搜索条件例如在google里输入 intext:百度将返回所有在网页正文部分包含"百度"的网页allintext:使用方法和intext类似

intitle:
和上面那个intext差不多,搜索网页标题中是否有我们所要找的字符例如搜索 intitle:百度将返回所有网页标题中包含"百度"的网页.同理allintitle:也同intitle类似

cache:
搜索google里关于某些内容的缓存,有时候也许能找到一些好东西哦

define:
搜索某个词语的定义,搜索 define:hacker,将返回关于hacker的定义

filetype:
这个我要重点推荐一下,无论是撒网式攻击还是我们后面要说的对特定目标进行信息收集都需要用到这个搜索指定类型的文件.例如输入 filetype:doc将返回所有以doc结尾的文件URL当然如果你找bak、mdb或inc也是可以的,获得的信息也许会更丰富:)

info:
查找指定站点的一些基本信息

inurl:
搜索我们指定的字符是否存在于URL中例如输入 inurl:admin,将返回N个类似于这样的连接:http://www.xxx.com/xxx/admin,用来找管理员登陆的URL不错allinurl也同inurl类似,可指定多个字符

site:
这个也很有用,例如 site:www.baidu.com将返回所有和baidu.com这个站有关的URL
对了还有一些操作符也是很有用的:
+把google可能忽略的字列如查询范围
-把某个字忽略
~同意词
.单一的通配符
*通配符，可代表多个字母
""精确查询

下面开始说说实际应用(我个人还是比较习惯用google.com,以下内容均在google上搜索),对于一个居心叵测的攻击者来说,可能他最感兴趣的就是密码文件了而google正因为其强大的搜索能力往往会把一些敏感信息透露给他们用google搜索以下内容:

有时候因为各种各样的原因一些重要的密码文件被毫无保护的暴露在网络上,如果被别有用心的人获得,那么危害是很大的下面是我找到的一个FreeBSD系统的passwd文件(我已做过处理):

同样可以用google来搜索一些具有漏洞的程序,例如ZeroBoard前段时间发现个文件代码泄露漏洞,我们可以用google来找网上使用这套程序的站点:
intext:ZeroBoard filetype:php

前面我们已经简单的说过可以用google来搜索数据库文件,用上一些语法来精确查找能够获得更多东西(access的数据库,mssql、mysql的连接文件等等).举个例子示例一下:

allinurl:bbsdata
filetype:mdbinurl:database
filetype:incconn
inurl:datafiletype:mdb

利用google完全是可以对一个站点进行信息收集和渗透的，下面我们用google对特定站点进行一次测试，www.xxxx.com是全国著名大学之一，一次偶然的机会我决定对其站点进行一次测试(文中所涉及该学校的信息均已经过处理，请勿对号入座:)
首先用google先看这个站点的一些基本情况(一些细节部分就略去了):
site:xxxx.com

从返回的信息中，找到几个该校的几个系院的域名：

http://a1.xxxx.com
http://a2.xxxx.com
http://a3.xxxx.com
http://a4.xxxx.com
顺便ping了一下，应该是在不同的服务器.(想想我们学校就那一台可怜的web服务器，大学就是有钱，汗一个)，学校一般都会有不少好的资料，先看看有什么好东西没:
site:xxxx.com filetype:doc

得到N个不错的doc，先找找网站的管理后台地址：
site:xxxx.com intext:管理
site:xxxx.com inurl:login
site:xxxx.com intitle:管理

超过获得2个管理后台地址：
http://a2.xxxx.com/sys/admin_login.asp
http://a3.xxxx.com:88/_admin/login_in.asp
还算不错，看看服务器上跑的是什么程序：
site:a2.xxxx.com filetype:asp
site:a2.xxxx.com filetype:php
site:a2.xxxx.com filetype:aspx
site:a3.xxxx.com filetype:asp
site:…
…

a2服务器用的应该是IIS，上面用的是asp的整站程序，还有一个php的论坛
a3服务器也是IIS，aspx+asp，web程序都应该是自己开发的，有论坛那就看看能不能遇见什么公共的FTP帐号什么的：
site:a2.xxxx.com intext:ftp://:

没找到什么有价值的东西，再看看有没有上传一类的漏洞：
site:a2.xxxx.com inurl:file
site:a3.xxxx.com inurl:load

在a2上发现一个上传文件的页面：
http://a2.xxxx.com/sys/uploadfile.asp
用IE看了一下，没权限访问，试试注射，
site:a2.xxxx.com filetype:asp

得到N个asp页面的地址，体力活就让软件做吧，这套程序明显没有对注射做什么防范，dbowner权限，虽然不高但已足矣，backashell我不太喜欢，而且看起来数据库的个头就不小，直接把web管理员的密码暴出来再说，MD5加密过，一般学校的站点的密码都比较有规律，通常都是域名+电话一类的变形，用google搞定吧

site:xxxx.com//得到N个二级域名
site:xxxx.comintext:*@xxxx.com//得到N个邮件地址，还有邮箱的主人的名字什么的
site:xxxx.comintext:电话//N个电话

inurl: 是駭客重要的搜尋方法，可搜到網址包括的關鍵字，例如填上 allinurl:login password 作搜尋，便會很易找到有 login 和 password 的網頁。

filetype: 是駭客專用語法，例如想找 mdb 的數據庫檔案，可用 password filetype:mdb 作搜尋，

Index of /admin
"Index of /" +password.txt

有些站長會將密碼儲存成 password.txt 檔案，如配合 index browsing 的弁遄A將 google 的關
鍵字串成 "Index of /" +password.txt 作搜尋，便找到很多 password.txt
以下還有更多輸入搜尋法，有時間可自行玩玩！
"Index of /admin"
"Index of /password"
"Index of /mail"
"Index of /" +passwd
"Index of /" +password.txt
"Index of /" +.htaccess
index of ftp +.mdb allinurl:/cgi-bin/ +mailto

administrators.pwd.index
authors.pwd.index
service.pwd.index
filetype:config web
gobal.asax index

allintitle: "index of/admin"
allintitle: "index of/root"
allintitle: sensitive filetype:doc
allintitle: restricted filetype :mail
allintitle: restricted filetype:doc site:gov

inurl:passwd filetype:txt
inurl:admin filetype:db
inurl:iisadmin
inurl:"auth_user_file.txt"
inurl:"wwwroot/*."


top secret site:mil
confidential site:mil

allinurl: winnt/system32/ (get cmd.exe)
allinurl:/bash_history

intitle:"Index of" .sh_history
intitle:"Index of" .bash_history
intitle:"index of" passwd
intitle:"index of" people.lst
intitle:"index of" pwd.db
intitle:"index of" etc/shadow
intitle:"index of" spwd
intitle:"index of" master.passwd
intitle:"index of" htpasswd
intitle:"index of" members OR accounts
intitle:"index of" user_carts OR user_cart
```
