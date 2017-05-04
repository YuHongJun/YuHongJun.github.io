---
author: Demi_YuHongJun
comments: true
date: 2016-06-07 18:42:32+00:00
layout: post
title: 在github pages网站下用jekyll制作博客教程
categories:
- Tech
tags:
- jekyll
- github
---
* 目录
{:toc}
---
### 安装流程

1. 要用github pages，首先要在github中建立一个基于你的用户名的repository: 比如说我，就要建立名为[yuhongjun.github.io](https://github.com/YuHongJun/YuHongJun.github.io)的repo。在以前的github版本中还需要在后台开启pages的功能，现在系统检测到这样的repo名称之后，会在setting中自动开启GitHub Pages的功能.
这样之后你就可以把这个repo克隆到本地随意进行修改了，在这个里面上传的网页就是你的网站的内容了，可以上传一个index.html试一试，这就是你的网站主页了。
关于GiuHub的使用，可以看几个比较好的入门教程：[GitHub](https://www.zhihu.com/question/20070065)
2. 之后我们就要在本地部署jekyll，jekyll的原理很简单。这是一个已经合成好的静态html网站结构，你用这个结构在username.github.io文件夹里面粘帖好所有文件。再把更新完的本地repo推送到GitHub的master branch里面，你的网站就更新建设完毕了。
首先你需要[ruby](https://www.ruby-lang.org/en/)来使用本地jekyll。Mac和Linux可以用Terminal配合[yum](http://yum.baseurl.org/)或者[brew](http://brew.sh/)这样的包管理器很方便的安装ruby。Windows下更是方便，可以直接中集成好的[Ruby installer](http://rubyinstaller.org/)来进行安装，文章里的就是传送门。

	安装完ruby，之后就是要安装[RubyGems](https://rubygems.org/pages/download)，gem是一个ruby的包管理系统，可以用gem很方便的在本地安装ruby应用。

	安装方法

	```
	//在RubyGems官网上下载压缩包，解压到你的本地任意位置
	//在Terminal中
	cd yourpath to RubyGems //你解压的位置
	ruby setup.rb

	```

3. 有了gem之后安装jekyll就很容易了，其实用过nodejs和npm的同学应该很熟悉这样的包安装，真是这个世界手残脑残们的救星。。。。。（楼主不自觉的摸了摸自己快残了的手）
安装jekyll，有了gem，直接在Terminal里面输入以下代码：

	```
	$ gem install jekyll 
	```
4. 好了，现在你的电脑已经准备完毕了。如果你是想自己捣鼓，可以根据这样的目录结构在你的username.github.io文件夹下建立以下目录结构：
	
	├── _config.yml

	├── _drafts

		|   ├── begin-with-the-crazy-ideas.textile
		|   └── on-simplicity-in-technology.markdown

	├── _includes

		|   ├── footer.html
		|   └── header.html

	├── _layouts

		|   ├── default.html
		|   └── post.html

	├── _posts

		|   ├── 2007-10-29-why-every-programmer-should-play-nethack.textile
		|   └── 2009-04-26-barcamp-boston-4-roundup.textile

	├── _site

	└── index.html

	
	你可以一个个依次建立起来，然后在自己编写一个你想要的博客。
5. 如果你只是个普通用户，只是想要一个模板然后开始写自己的博客。那就很容易了，有几个可以简单开始的模板。
	-	[https://github.com/poole/poole](https://github.com/poole/poole)极简风格的模板
    -   [http://jekyllthemes.org/](http://jekyllthemes.org/)	jekyll的模板网站，可以找到各式各样你喜欢的模板。
6. 下载完了模板，可以吧里面的内容解压到你自己的网站目录底下。这时候你可以测试一下：

	```
	$ cd you website path //cd到你的网站目录下
	$ jekyll serve
	//一个开发服务器将会运行在 http://localhost:4000/
	//你就能在本地服务器看到你用模板搭建的网站了
	```
7. 这时候可以看一下jekyll的设置，让你把模板变成你自己个性化的内容。在网站根目录下面找到	**_config.yml**,这里会有几个比较关键的设置：
里面的permalink 就是你博客文章的目录结构，可以用pretty来简单的设置成日期+文章标题.html，也可以用自己喜欢的结构来设置。
记得把encoding 设置成utf-8，这样有利于中英文双语的写作和阅读。
8. 到这里你就可以开始写博客了，所有的文章直接放在**_posts**文件夹下面，格式就是我们之前提到的markdown文件，默认的格式是.md和.markdown文件。每篇文章的开始处需要使用yml格式来写明这篇文章的简单介绍，格式如下：

	```
		---
        author: Demi_YuHongJun
        comments: true
        date: 2017-04-22 9:42:32+00:00
        layout: post
        title: React 常见的面试题
        categories:
        - Tech
        tags:
        - javascript
        - react
        ---
	```
layout就是post，让jekyll知道你这是一篇post，很直观。需要注意的是里面的**date**，必须按照yml的语法来写，否则就会出现编译错误。可以只用**YYYY-MM-DD**来显示日期，也可以像我一样在后面加上 **HH:MM:SS+00:00** 来表示更具体的时间。
9. 到此为止可以开始尽情的写博客了，用GitHub软件同步到你的repository里面，网站上面就可以进行正常的显示了。如果说要添加一下有用的extra功能的话，评论和相关文章这两个功能比较多人会关注。
评论我们可以用[Disqus](https://disqus.com/)国内应该也有类似的网站，到Disqus注册一个账号，选择添加评论区域到自己的网页，你将会的得到类似的代码：

	```
	<!-- Add Disqus comments. -->
	<div id="disqus_thread"></div>
	<script type="text/javascript">
	  /* * * CONFIGURATION VARIABLES: EDIT BEFORE PASTING INTO YOUR WEBPAGE * * */
	  var disqus_shortname = '<USERNAME>'; // required: replace example with your forum shortname
	  var disqus_identifier = "{{ site.disqusid }}{{ page.url | replace:'index.html','' }}";
		
	  /* * * DON'T EDIT BELOW THIS LINE * * */
	  (function() {
	    var dsq = document.createElement('script'); dsq.type = 'text/javascript'; dsq.async = true;
	    dsq.src = '//' + disqus_shortname + '.disqus.com/embed.js';
	    (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(dsq);
		  })();
	</script>
	<noscript>Please enable JavaScript to view the <a href="http://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
	<a href="http://disqus.com" class="dsq-brlink">comments powered by <span class="logo-disqus">Disqus</span></a>
	```
根据不同的模板，把代码添加到**_post/post.html**或者**_include/post.html**里你的文章底下，那当这篇文章被访问时，下方就会有评论区了

10. 相关文章的功能也比较好做，jekyll本来就集成了**site.related_posts**的功能，自动会寻找相关内容的文章，在你的post代码下面融入以下代码：

	```
	<aside class="related">
	  <h2>Related Posts</h2>
	  <ul class="related-posts">
	    {% for post in site.related_posts limit:3 %}
	    <li>
	      <h3>
	        <a href="http://yuhongjun.github.io/{{ site.BASE_PATH }}/{{ post.url }}">
	          {{ post.title }}
	          <small><time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date_to_string }}</time></small>
	        </a>
	      </h3>
	    </li>
	    {% endfor %}
	  </ul>
	</aside>
	```
	你每篇文章下面就会有三个相关文章的链接了。

[http://rsms.me/](http://rsms.me/)
