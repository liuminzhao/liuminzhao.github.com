---
layout: post
title: "remote r package on mac"
description: ""
category: 
tags: [mac, R]
---
{% include JB/setup %}

Install R Package on Mac through SSH 
==========

All on remote 

	ssh -Y username@address

# Download #

	curl -O packageaddress
	
# Install #

	R CMD INSTALL packagename lib
	R CMD INSTALL multicore_0.1-7.tgz ~/Documents/Rpackages/

