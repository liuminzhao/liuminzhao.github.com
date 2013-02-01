---
layout: post
title: "remote on mac"
description: ""
category: 
tags: [ssh, mac, vnc]
---
{% include JB/setup %}

SSH and VNC on mac
==========

# Xquarts #

install `xquartz` on both local and remote machine

# Remote #

system preference > sharing > remote login 

edit `/etc/sshd_config` or `/Private/etc/sshd_config` as sudo  and make 

	X11Forwarding yes

restart sshd on mac (uncheck and recheck the remote login). 

# Local #

edit `/etc/ssh_config` 

	ForwardX11 yes 

then use the `-Y` on ssh 

# VNC #

system preference > Sharing > screen sharing 

in the remote mac, hit 

	Command + K  
	
and type `vnc://` 
