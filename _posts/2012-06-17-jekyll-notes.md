---
layout: post
title: "jekyll notes"
description: ""
category:
tags: [jekyll]
Time-stamp: "liuminzhao 02/06/2014 11:46:49"
---
{% include JB/setup %}

Jekyll Bootstrap
==========

[link](http://jekyllbootstrap.com/usage/jekyll-quick-start.html)

# Install  #

    gem install jekyll

follow [link](http://jekyllbootstrap.com/index.html#start-now)

	$ git clone https://github.com/plusjade/jekyll-bootstrap.git liuminzhao.github.com
	$ cd liuminzhao.github.com
	$ git remote set-url origin git@github.com:liuminzhao/liuminzhao.github.com.git
	$ git push origin master

# Post #

	$ rake post title="helloworld"

or

	$ rake post title="hellworld" date="2012/06/17"

## Cite ##

	<ul class="posts">
	{% for post in site.posts %}
	<li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
	{% endfor %}
	</ul>

# Page #

	$ rake page name="about.md"
	$ rake page name="pages/about.md"

Create a page with a “pretty” path:

	$ rake page name="pages/about"

this will create the file: ./pages/about/index.html

# Publish #

	$ git add .
	$ git commit -m "new"
	$ git push origin master

# [Theme](http://themes.jekyllbootstrap.com/) #

	$ rake theme:install # install theme
	$ rake theme:package # package theme
	$ rake theme:switch

	$ rake theme:install git="git://github.com/jekyllbootstrap/theme-mark-reid.git"

or downlaod zip into `./_theme_packages` and

	$ rake theme:install name="name"

* [Mark-Reid Theme](http://mark.reid.name/info)

# Post Attributes #

	layout: page
	title :  Hello World
	categories : [lessons, beginner] #This defines the category hierarchy lessons/beginner”.
    tagline: Supporting tagline
	tag: [ ]

# Preview #

	jekyll serve
	jekyll serve --watch : to rebuild after every save

[localhost](http://localhost:4000/)

# API #

[JB API](http://jekyllbootstrap.com/api/bootstrap-api.html)

# 关于域名 #

在本地代码库里新建名为CNAME的文本文件，把域名地址放进去。假设你的域名是domain.com，可以用命令

    echo 'domain.com' > CNAME

然后

    git add CNAME
	git commit -am "CNAME file added"
	git push

在 godaddy.com 里修改 DNS A 指向 207.97.227.245 (github 域名).

# Github 不更新问题 #

清除 cache, 刷新.

# 中文列表乱 #

<http://yangzetian.github.com/2012/03/28/markdown/>

> 上网查后得知原来是 jeklly 默认 markdown 引擎 maruku 的问题，将引擎改为 rdiscount 即可。做法是修改 `_config.yml` 文件，在 pygments: true 上面添加一行 `markdown: rdiscount`

同时, 在默认的 maruku 下, 在 gist 之后的文字有时候会显示不出来. 在改成 rdiscount 后, 就好了.

# Math/LaTeX #

[reference 1](http://jiyeqian.github.com/2012/07/host-your-pages-at-github-using-jekyll/)

[reference 2](http://yanping.me/cn/blog/2012/03/10/octopress-with-latex/)

[reference 3](http://stackoverflow.com/questions/10987992/using-mathjax-with-jekyll)

	<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>

(Those configuration options allow you to use more tex notation to start your math environment, such as `\begin{equation}`, etc).

<script src="https://gist.github.com/3976574.js?file=mathjax.js"></script>

Usage:

	$\alpha$

or

	$$
	\alpha
	$$

supported : <http://docs.mathjax.org/en/latest/tex.html>

Update:

seems need one more `\` to make it work

# Update modified date #

In prefix, add

	Time-stamp: " "

or

	modified: 2013/07/01

then in `_includes/themes/hooligan/post.html`, update

	{% if page.Time-stamp %}
	<h4>Modified</h4>
	<div class="date">
	<span>{{page.Time-stamp}}</span>
	</div>
	{% endif %}

With pretty date format:

	{{ page.Time-stamp | date: "%-d %B %Y" }}

for `9 September 2013`.

# change auto puts when creating new post and page #

modify the `Rakefile` under root directory

	post.puts 'Time-stamp: " "'

for task:post

# Put page in navigation #

	layout: page
	group: naivgation

# Show Latest Posts #

	{% for post in site.posts limit:1 %}
	... Show the post ...
	{% endfor %}
	<h1>Recent Posts</h1>
	{% for post in site.posts offset:1 limit:2 %}
	... Show the next to posts ...
	{% endfor %}

use `limit` and `offset`.

Second method: <https://gist.github.com/nimbupani/1421828>
