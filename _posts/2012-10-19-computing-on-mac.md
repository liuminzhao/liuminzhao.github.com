---
layout: post
title: "Computing on Mac"
description: ""
category: 
tags: [mac]
---
{% include JB/setup %}

Mac for Computing
==========

# How to ssh to Mike's machine #

	ssh username@mike's address
	
# ssh with X window forwarding #

- Install [xquartz](http://xquartz.macosforge.org/) on both local and remote machine. (I have set up configuration and installed software on Mike's machine) 
- Edit `/etc/ssh_config` in your local mac, change the following

	    ForwardX11 yes
		
then use `ssh -Y` to connect.

# How to run R in the background #

After you use `ssh` to log in Mike's machine, type 

	screen 
	
to open a session, which can run in the background. At this time you can even turn down your local laptop, and your remote session is still on. 

To fetch your session, next time you log on Mike's machine, type

	screen -r 
	
or 

	screen -d -r 
	
you will get what you left last time. Type `man screen` for more options of `screen`. 

After you open the `screen` session, you can run your R code in the background:

	R CMD BATCH --no-save --no-restore infile outfile &
	
See [this page](http://www.stat.ufl.edu/system/R-background.shtml) for detail. 

# How to transfer file using scp #

	scp yourlocalfile username@mike's address:~/Documents
	
You can specify the remote destination folder as you want. 

To get file back 

	scp username@mike's address:~/yourremotefile yourlocaldirectory

For directory transfer, add `-r` option

	scp -r 
	
# How to install R package on Mike's machine #

So far, I have trouble with installing R package on Mike's machine, but I figured out one way, which might not be the perfect, but it works. 

When you log on the remote mac machine, download the desired R package from cran or transfer your downloaded R package to Mike's machine using `scp` from your local machine. For example, if I want to install `xtable` package, I googled and found [this page](http://cran.r-project.org/web/packages/xtable/index.html). Then on Mike's machine, I type:

	curl -O http://cran.r-project.org/bin/macosx/leopard/contrib/r-release/xtable_1.7-0.tgz
	
where the url is the MacOS X Library download address on [previous webpage](http://cran.r-project.org/web/packages/xtable/index.html). 

	R CMD INSTALL xtable_1.7-0.tgz ~/Documents/Rpackages/
	
where `Rpackages` is the folder I make to install R packages. Now you should be able to load R package in R console (`library(xtable)`). 

# Software #

* Emacs

** emacsforosx

** Aquamacs

** Emacs Mac Port

** homebrew

* homebrew/macport/flink

* R 

* xquartz

* LaTeX

** Mactex

* C and Fortran

** Xcode

** gfortran

* Iterm2

# Tips #

check for cpu

	top -u -s5 : every 5s check cpu

check cpu usage, ordered by cpu, and list username, cpu, time, which command. 

	top -o cpu -stats user,cpu,time,command

Standby vs hibernate (deep sleep):

	sudo pmset -a standbydelay 42000

# Your .profile #

Make `ls` colorful

	alias ls='ls -G'

Make `iterm` tab name change automatically

	export PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME%%.*}\007"'
	

