---
layout: post
title: "c and fortran on mac"
description: ""
category: 
tags: [c, fortran, mac]
---
{% include JB/setup %}

How to Install C and Fortran Compiler on Mac
==========

# C #
 
reference: <http://www.macobserver.com/tmo/article/install_the_command_line_c_compilers_in_os_x_lion> 

1. Downlaod and install **Xcode** from App Store. 
2. Lauching **Xcode**, go to Preferences and select the Downloads pane, then Components. There, in the list of candidate items will be the Command line tools. Click “Install.”. 
3. Once done, open Terminal, change to `/usr/bin` and type `./gcc -v` to check if gcc has been installed in command use.

# Fortran #

Reference: <http://r.research.att.com/tools/> and <http://www.webmo.net/support/fortran_osx.html>

1. First install **Xcode** as in C part
2. Download [gfortran-4.2.3.dmg](http://r.research.att.com/gfortran-4.2.3.dmg) and install. or may install [gfortran-lion-5666-3.pkg](http://r.research.att.com/gfortran-lion-5666-3.pkg) which is GNU Fortran 4.2.4 for Mac OS X 10.7 (Lion). 
