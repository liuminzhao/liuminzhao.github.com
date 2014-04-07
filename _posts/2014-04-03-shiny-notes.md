---
layout: post
title: "shiny notes"
description: ""
category:
tags: [R, shiny, twitch]
Time-stamp: "liuminzhao 04/03/2014 13:18:36"
---
{% include JB/setup %}

An Example of Shiny Server on Amazon EC2
==============

# Sample

[Twitch Top Hearthstone Streamer](http://ec2-54-227-21-66.compute-1.amazonaws.com:3838/app1/)

# Reference

1. <https://github.com/rstudio/shiny-server>
2. <http://davetang.org/muse/2014/01/03/using-shiny/>
3. <http://trestletechnology.net/2013/02/deploying-shiny-server-on-amazon-ec2/>
4. <http://www.stat.yale.edu/~jay/EC2/CreateFromScratch.html>

# Install

	sudo apt-get install r-base
	sudo apt-get install gdebi-core
	wget http://download3.rstudio.org/ubuntu-12.04/x86_64/shiny-server-0.4.0.8-amd64.deb
	sudo gdebi shiny-server-0.4.0.8-amd64.deb
	sudo su - \
	-c "R -e \"install.packages('shiny', repos='http://cran.rstudio.com/')\""

## configure

create directory

	sudo mkdir /etc/shiny-server
	sudo nano /etc/shiny-server/shiny-server.conf

<script src="https://gist.github.com/liuminzhao/9959639.js"></script>


## port

On Amazon EC2 instance, turn on the TCP port 3838 (security -> rules):

# Start Server

	sudo start shiny-server
	sudo restart shiny-server

open `http://<hostname>:3838/app_name`

# Example

<script src="https://gist.github.com/liuminzhao/9959769.js"></script>

The python web scraping script by Twitch API:

<script src="https://gist.github.com/liuminzhao/9437693.js"></script>

# Troublesome

## Package not found

<http://stackoverflow.com/questions/16065805/packages-missing-in-shiny-server?rq=1>.

> Compare the output of .libPaths() in both cases and adjust accordingly in the server instance / your script.

> You may for example have the packages in "your" R package directory which the server cannot access. System-wide package installations are preferable in cases like this -- and are e.g. the default on Debian / Ubuntu.

	sudo R
	install.package('plyr', .libPaths()[3])
