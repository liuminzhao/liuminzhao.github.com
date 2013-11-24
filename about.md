---
layout: page
title: About
header: About
group: navigation
Time-stamp: "liuminzhao 11/24/2013 16:43:46"
---
{% include JB/setup %}

# Minzhao Liu

## Bio

<div style="float:left"><img src="http://i.imgur.com/NSyDqih.jpg"
style="float:left;margin:0 10px 10px 0" width="15%"></div>

Currently I am a Ph.D. candidate in
[Statistics](http://www.stat.ufl.edu/) at
[University of Florida](http://www.ufl.edu/).  I am also working as a
research assistant for my advisor
[Dr. Mike Daniels](http://www.sbs.utexas.edu/mjdaniels/) at
[University of Texas at Austin](http://www.utexas.edu).  My research
topic includes quantile regression in frequentist and Bayesian
framework and methodology for (incomplete) longitudinal data.
Previously, I worked as an intern for
[Educational Testing Service](http://www.ets.org/) (ETS) supervised
under Dr. Yi-Hsuan Lee and Dr. Alina von Davier. Before coming to US,
I had a B.S. in Mathematics at
[Fudan University](http://www.fudan.edu.cn/englishnew/), Shanghai,
China.

## Projects

### Detection of Unusual Test Administrations Using a Linear Mixed Effects Model

This project is done during my internship in [ETS] during 2011 summer
with Dr. Yi-Hsuan Lee and Dr. Alina von Davier. It was presented in
International Meeting of the Psychometric Society
[IMPS](http://www.psychometrika.org/) 2012 conference in Lincoln,
Nebraska and will appear as a chapter in the book, New Developments in
Quantitative Psychology.

The project is to fit a mixed effects model based on a training
dataset, find the relationship between test-takers' scores and
background, then predict the mean score of certain test administration
to detect if there is any unusualness.
[R code](https://liuminzhao@bitbucket.org/liuminzhao/ets-intern.git)

### Bayesian Quantile Regression using Mixture of Polya Trees

In this paper, we adopt a mixture of Polya Tree prior for the
regression error to nonparametrically capture the shape of error
distribution, thus make inference for quantile regression parameters.
It was presented in [ENAR](https://www.enar.org/) 2011 and will serve as
a chapter in my PhD dissertation. Code can be
found here. [R package](https://github.com/liuminzhao/bqrpt.git)

### Quantile Regression in the Presence of Monotone Missingness with Sensitivity Analysis

This paper develops new approach to fit quantile regression for
longitudinal data with monotone missingness and how to do sensitivity
analysis. [R package](https://github.com/liuminzhao/qrmissing.git)

## My Interest

- Sports

	I am a big fan for all kinds of sports. I used to play *basketball*
    (guard) and *soccer* (right fullback) while I am in China. And I
    turned to love American *football* by inspiration from *Tim Tebow* and
    our Football team, *Gators*. Every Sunday morning, we play our
    regular *flag football* in Austin and I usually take wide receiver
    or running back. I like *fishing* also, but just a beginner. The
    biggest achievement while I was in Florida is four catfish in Lake
    Wauberg. And while I was traveling in Minnesota, I had a chance to
    *ski*. It is so fun but it seems little chance for me to practice since
    I usually stay in south.

- Coding

	I also like computer languages. I use *R*, *SAS*, *Python* and
    *fortran* for my research, and use *Markdown*, *jekyll*, *zsh* for
    my personal notes and host them on [Github](https://github.com/)
    and [bitbucket](https://github.com/). I am also learning Android
    programming in order to build an app to make fun of my
    friend. Usually I learn languages on
    [coursera](https://www.coursera.org/) and
    [stackoverflow](http://stackoverflow.com/) or by
    myself. (Stackoverflow is very addictive.)
    [myprofile](http://stackoverflow.com/users/1453751/liuminzhao)

	Currently the coding environment I am using is under OS X, Emacs and Zsh (not vi-hater). You can also find lots of emacs notes in this website.

- Game

	During my leisure time, I play computer games. I am a big fan of [Blizzard](http://us.blizzard.com/en-us/). And the most recent game I am on is [Hearthstone](http://us.battle.net/hearthstone/en/).

## Background

I was born and raised in Shanghai, China, a beautiful and rapid
developing city. Before coming to US, I studied Mathematics at Fudan
University as undergraduate in Shanghai. For the first few years in
US, I lived in Gainesville, FL beginning my PhD at University of
Florida and I am very proud of being a Gator. Then in 2012, I moved to
Austin, TX following my advisor, thus became a half Longhorn.

## About This Site

This site is an experiment of blogging by combination of Jekyll,
Markdown and Github pages. I blogged my notes of study, life and any
other stuff, hosted them under Github and write as a hacker. As I am
graduating in 2014 summer, I construct more on this site to give more
information about myself.

## Contact

- Email: liuminzhao@gmail.com

<!-- <li class="divider-vertical"></li> -->
<li>
<a href="https://github.com/{{ site.author.github }}" class="zocial github icon" target="_blank">
<span class="hidden-desktop">Github</span>
</a>
<a href="https://plus.google.com/{{ site.author.googleplus }}" class="zocial googleplus icon" target="_blank">
<span class="hidden-desktop">Google+</span>
</a>
<a href="http://www.linkedin.com/in/{{ site.author.linkedin }}" class="zocial linkedin icon" target="_blank">
<span class="hidden-desktop">LinkedIn</span>
</a>
</li>

{% if page.Time-stamp %}
<h4>Updated by:</h4>
<div class="date">
<span>{{page.Time-stamp | date: "%-d %B %Y"}}</span>
</div>
{% endif %}

[ETS]: http://www.ets.org/
