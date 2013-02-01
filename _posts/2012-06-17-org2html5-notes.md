---
layout: post
title: "org2html5 notes"
description: ""
category: 
tags: [org-mode, html5, slides]
---
{% include JB/setup %}

使用 Org-mode 制作 html5 幻灯片
==========

今天要讲的是怎么使用 Emacs 的 org-mode 来制作 [html5](slides.html5rocks.com/) 的 slides. 

# 安装 #

首先下载 [org-html5presentation.el](https://gist.github.com/509761)

# 问题 #

模板的 bullets 会有问题, 在生成的 html5 slides 里会有乱码, 而不是正常的 bullets. 所以按照[知竹轩](http://wuyang.yangsheep.net/#sec-2-2-1-10)的笔记, 修改 org-html5presentation.el 的源码: 

* 修改 li 的 list-style 为 disc
* 清空 li:before 的内容

       > li {
		 >   list-style: disc;
		 >   padding: 10px 0;
		 > }
		 > .summary li::before, .sub-summary li::before, .bullets li::before {
		 > }

# 使用 #

1. 把 el 文件放到 .emacs 载入路径

2. 在 .emacs 文件里写入

         (require 'org-html5presentation)

3. 重启 emacs

4. 在 org 文件下 

         M-x org-export-as-html5presentation

or

    M-x org-export-as-html5presentation-and-open

## Markdown to Org ##

	pandoc -t org input.md -o output.org

## 模板 ##

1. 插入模板

	C-c C-e t 

2. 快速模板

	\< s/e/q/v/c/l/L/h/a/i Tab

3. 也可使用 yasnippet
 
## 插图 ##

### 在 org-mode 里显示图片 ###

[iimage.el](http://www.netlaputa.ne.jp/~kose/Emacs/iimage.html)

	M-x iimage-mode 

	C-l

### 图片属性 ###

* 插入图片

	fdaf
	[[[file:test.png] ] ]
	sdaf
	
* 所有的属性都可以在[这里](http://www.w3schools.com/tags/tag_img.asp)看到. 一般的格式为

        #+ATTR_HTML: alt="" width="" style="border:2px solid black; float:left(right); margin:20px 20px ;" align="right"

* 所有图片展示在一列, 并列展示 

	style="display:inline; margin:10px;"

* 显示标题

	 #+CAPTION: TEST
	 #+ATTR_HTML: title="fs"
	 图片

## 表格 ##

基本同图片, 不过有特殊格式, 例如:

	#+ATTR_HTML: border="2" rules="all" frame="border" 

## 数学公式 ##

参见 [Mathjax](http://orgmode.org/mathjax/docs/html/tex.html), 默认方法只识别 $$ 符号. 若要使用 $ 在 inline 里, 必须
特别指示. Mathjax 识别的 LaTeX 符号请翻越上述链接. 

### Math Font ###

	\small
	\tiny
