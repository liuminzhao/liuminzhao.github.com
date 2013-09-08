---
layout: post
title: "linux notes"
description: ""
category:
tags: [linux]
Time-stamp: "liuminzhao 09/06/2013 22:21:10"
---
{% include JB/setup %}

# grep #

[reference](http://bbs.chinaunix.net/thread-692640-1-1.html)

<http://cloudbbs.org/forum.php?mod=viewthread&tid=16867>

basic usage:

	grep [options] pattern [file]

all file contains 'boss'

	grep -l 'boss' *

show line number

	grep -n 'boss' file

## Options ##

`-n`: show +- n lines

	grep -2 pattern file

`-c`: print line number

`-i`: inore case sensitive

`-l`: show file list

`-w`: word regrexp

## Examples ##

	ls -l | grep '^a' 通过管道过滤ls -l输出的内容，只显示以a开头的行。
	grep 'test' d* 显示所有以d开头的文件中包含test的行。
	grep -w pattern files ：只匹配整个单词，而不是字符串的一部分(如匹配‘magic’，而不是‘magical’)，
	grep -C number pattern files ：匹配的上下文分别显示[number]行，
	grep pattern1 | pattern2 files ：显示匹配 pattern1 或 pattern2 的行，
	grep pattern1 files | grep pattern2 ：显示既匹配 pattern1 又匹配 pattern2 的行。

# Diff #

Compare 2 folders:

	diff -bur folder1/ folder2/

Two column

	diff -y

or `colordiff`

	colordiff -y f1 f2 | less

`less` for browsing slowly.

[xahlee](http://xahlee.info/UnixResource_dir/unix_shell_text_processing.html)

# Crontab #

Schedule a routine background job at a specific time

	crontab -l : list
	crontab -e : edit

Format:

	MIN HOUR DOM MON DOW CMD
	0-59 0-23 1-31 1-12 0-6
	30 08 10 06 * /home/ramesh/full-backup
	00 11,16 * * * /home/ramesh/bin/incremental-backup : twice a day
	00 09-18 * * * /home/ramesh/bin/check-db-status : working hour
	00 09-18 * * 1-5 /home/ramesh/bin/check-db-status : work day working hour
	* * * * * CMD : every minute

Others:

1. When you specify */5 in minute field means every 5 minutes.
2. When you specify 0-10/2 in minute field mean every 2 minutes in the first 10 minute.
3. Thus the above convention can be used for all the other 4 fields.

	*/10 * * * * /home/ramesh/check-disk-space : every 10 min

Email:

Put

	MAILTO="email@domain.com"

on the top

Change default editor:

One time:

	EDITOR=nano crontab -e

Ever:

	export EDITOR=nano

# Screen #

	c: create
	C-A n: next
	p: previous
	A: rename
	S: split horizontal
	| or V: vertical
	tab: jump
	X: remove current
	Q: remain current

in `~/.screenrc` put:

	escape ^||
	caption always "%{= kw}%-w%{= BW}%n %t%{-}%+w %-= @%H - %LD %d %LM - %c"

to avoid conflict with `emacs`.

# Regex #

## Syntax ##

	. : any
	^: start of the line
	$: end of the line
	[]: indicate a set of char
	[^T] : complement set
	\d == [0-9]
	\D = [^0-9] ; non digit
	\s : any whitespace
	\S: any non whitespace
	\w: [a-zA-Z0-9_]
	\W : [^a-zA-Z0-9_]

## Example ##

	[Nn]ick
	[a-c]
	. = [-.?+%$A-Za-z0-9...]  # [] means pick just one

## Alternation ##

	a|b|c = [a-c]

## Grouping ##

	0abc+0 :
	0(abc)+0

## back reference ##

	Set(?:Value)?

## Positive and Negative Lookhead  ##

	q(?!u) : negative
	q(?=u) : positive

## Lookbehind ##

	(?<!a)b : not preceded by a
	(?<=text)b:

## Greedy ##

`+` and `*` are greedy, use `?` after them to make them not greedy

	x*?

## Repeating ##

	*: zero or more {0,}
	+: at least one {1,}
	? : once or none {0,1}
	{m,n}: m-n times

## Work Lock ##

	\bgrep\b : 'grep' only with space before and after

# Shell #

<http://cloudbbs.org/forum.php?mod=viewthread&tid=13681>

100 Most used :

- `echo "aa" > test.txt`
- `du -ah` for size , `du -sh` the sum of size
- `echo '1+2' | bc -l` : for math
- `uname -a` : kernel detail
- `time command`: time for command
- `ls -lrt`: sort by time
- `history -c`: clear history
- `tree`: show tree
- `echo $[5*5]` : math
- `free -m` : show memory
- `uptime` : how long the computer has run
- `export`: show all the env variable
- `echo $PATH`: show single variable
- `clear` : `C-l`
- `cmp file1 file2`: compare
- `cal` : calendar
- `echo "AaDCbd23" | tr "[A-Z]" "a-z"` : upper case to lower case,
- `tr -c b-d =`: replace letters other than b-d by `=`
- `bc`: go to math
- `last` : list record for login
- `paste -sd '|||\n' test` : change every 4 lines to 1 line and use `|` to separate
- `wget -c` : continiously download
- `touch test.txt`

# zsh #

file rename:

	zmv '(*).txt' '$1.html'

osx

	man-preview
	quick-look
	pfd: path finder
	cdf: cd to finder

# Email #

	mail -s 'subject' liuminzhao@gmail.com
	echo "blabla" | mail -s "text" liuminzhao@gmail.com

# Trick #

Yoda: `if ('blue' == col)`


# Sed #

find and delete all lines with string pattern in all files:

	sed -i.bak '/String/d' *

# Scp #

scp multiple files: must quote

	scp ...:"~/*.R" .

# Check login history #

	login

# At(to schedule task once) #

Reference:

1. <http://superuser.com/questions/43678/mac-os-x-at-command-not-working>
2. <http://www.ibm.com/developerworks/library/l-job-scheduling/index.html>
3. <http://www.simplehelp.net/2009/05/04/how-to-schedule-tasks-on-linux-using-the-at-command/>

`crontab` to schedule task repeatedly, `at` is used to schedule task once.

Note `at` or `atrun` is disabled on mac by default. So first

	sudo launchctl load -w /System/Library/LaunchDaemons/com.apple.atrun.plist

To use `at`:

to see if `atd` is running at daemon:

	ps -ef | grep atd

schedule from a file script at a specific time:

	at -f shellscript.sh -v 18:30

Time can also be :

	10am tomorrow
	now
	tuesday
	2:40
	next week
	now+2

To check queue;

	at -l
	atq

To remove tasks:

	at -r
	atrm

Check task content

	at -c #

# find #

<http://cloudbbs.org/forum.php?mod=viewthread&tid=16867>

basic usage:

	find [path] [expression]
	find [path] -options [-print -exec -ok ...]
	find [path] test
		options
		criteria
		action

`ok` is similar to `exec`, but it will ask you first.

## options ##

`-name`

`-user`

`-mtime -n +n`: modified time, `-n` : within n days, `+n` : before n days

	find / -mtime -5 -print

`-newer file1 ! file2`: modified after file1 and older than file2

`-type`:

	d: directory
	f: normal file
	l: link file

`-size n`

## xargs ##

	find . -type f -print | xargs file
	find / -name "core" -print | xargs echo "" >/tmp/core.log
	find . -type f -print | xargs grep "hostname"
	find ./ -mtime +3 -print|xargs rm -f –r
	find ./ -size 0 | xargs rm -f &

## command ##

	find ./ -size 0 -exec rm { } \;  # remove files with size 0
	find . -type f -exec ls -l { } \;
	find ./ -size 0 | xargs rm -f &

## Examples ##

	find ./ -size 0 -exec rm { } \;  # remove files with size 0
	rm -i 'find ./ -size 0'
	find ./ -size 0 | xargs rm -f &
	find . -type f -exec ls -l { } \;
	find /log -type f -mtime +5 -exec rm { } \;

# chown #

change ownership:

	chown server:server folder

# ps #

can show status of current process:

	ps -A | grep -i ssh
