---
layout: post
title: "Notes for Mutt"
description: ""
category: 
tags: [Mutt, Emacs]
---
{% include JB/setup %}

Notes for Mutt
==========

# Reference #

* <http://jason.the-graham.com/2011/01/10/email_with_mutt_offlineimap_imapfilter_msmtp_archivemail/>
* <http://www.adamjiang.com/archives/858>
* <http://pbrisbin.com/posts/mutt_gmail_offlineimap>
* <http://www.imtxc.com/blog/2012/04/22/use-gmail-plus-mutt-plus-msmtp-plus-offlineimap/>

# General #

mutt + offlineimap + imapfilter + msmtp 

# offlineimap #
	
	[general]
    # NOTE: cronjob calls the quiet UI with -u
	ui = ttyui
	accounts = Stat

    # [Account GMail]
    # localrepository = Gmail-Local
    # remoterepository = Gmail-Remote
    # autorefresh = 5

    [Account Stat]
	localrepository = stat-local
	remoterepository = stat-remote

	[Repository stat-local]
	type = Maildir
	localfolders = ~/Mail/Stat

    # Translate names from local names to remote names:
    # This one does:
    # 1. Capitalizes all the folder names
    # 2. Changes any underscores to spaces
    # 3. Changes Inbox -> INBOX
    nametrans = lambda foldername: re.sub('Inbox', 'INBOX',
	re.sub ('_', ' ', foldername.capitalize()))

	[Repository stat-remote]
	type = IMAP
	maxconnections = 2
	remotehost = eelpout.stat.ufl.edu
	remoteuser = liuminzhao
	remotepass = secret
	remoteport = 993
	ssl = yes

    # Translate remote names to local names:
    # This one does:
    # 1. Transforms names to lowercase
    # 2. Replaces spaces with underscores
    nametrans = lambda foldername: re.sub (' ', '_', foldername.lower())
    # [Repository Gmail-Local]
    # type = Maildir
    # localfolders = ~/Mail/GMail

    # [Repository Gmail-Remote]
    # type = Gmail 
    # remoteuser = liuminzhao@gmail.com
    # remotepass = secret
    # realdelete = no
    # keepalive = 30
    # holdconnectionopen = yes

    # # "[Gmail]/Some Folder" --> some_folder
    # nametrans = lambda folder: re.sub('^inbox$', 'INBOX',
    #                            re.sub(' +', '_',
    #                            re.sub(r'.*/(.*)$', r'\1', folder).lower()))

# msmtp #

	.msmtprc

# sort #

# signature #

	.signature

# refressh #

	#!/bin/bash
	PID=$(pgrep offlineimap)
	[[ -n "$PID" ]] && kill $PID
	offlineimap -o -u quiet &>/dev/null &
	exit 0

	chmod +x /usr/local/bin/syncmail.sh
	
# auto complete , contacts, google#

	sudo apt-get install googlecl
	
<http://chsc.wordpress.com/2011/06/07/mutt-query-googlec/>

worked way:

<http://pypi.python.org/pypi/goobook/1.4alpha4>

put in muttrc : 

	set query_command="goobook query '\%\s'"

	C-t

# Short cut #

# Muttrc #

	.muttrc

# Emacs #

<http://emacs-fu.blogspot.com/2009/01/e-mail-with-emacs-using-mutt.html>

	(server-start)
	
in muttrc 

	set editor="emacsclient +8 \%\s -a emacs" 

## post mode ##

	C-c C-c to send mail 

## el ##

# Gmail ssl #

<http://www.adamjiang.com/archives/858>

# Mailcap #

	text/html;  w3m -v -F -T text/html \%\s ; nametemplate=\%\s.html; copiousoutput
	application/pdf; evince \%\s
    #image/jpg; feh \%\s
    #image/jpeg; feh \%\s
    #image/png; feh \%\s
    #image/gif; feh \%\s
    #image/tiff; feh \%\s
	image/*; feh \%\s

in muttrc
	
	auto_view text/html
	
# Search #

* <http://www.calmar.ws/mutt/>
* <http://www.mutt.org/doc/devel/manual.html#patterns>

* `~b word ~d <2w`      |body word, in 2     
* `~f link ~b math`     |from, body          
* `~F ~f link ~b word`  |F tagged, from, body
* `~f link =b math`     |=exact              
* `~f gart ! ~f css`    |not from css        
