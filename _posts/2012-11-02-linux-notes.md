---
layout: post
title: "linux notes"
description: ""
category: 
tags: [linux]
---
{% include JB/setup %}

# grep #

[reference](http://bbs.chinaunix.net/thread-692640-1-1.html)

all file contains 'boss'

	grep -l 'boss' * 

show line number 

	grep -n 'boss' file
	
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
	
# Regex #

## Syntax ##

	. : any 
	^: start 
	$: end
	[]: indicate a set of char
	\d == [0-9]
	\D = [^0-9] ; non digit
	\s : any whitespace
	\S: any non whitespace
	\w: [a-zA-Z0-9_]
	\W : [^a-zA-Z0-9_]

## Repeating ##

	*: zero or more {0,}
	+: at least one {1,}
	? : once or none {0,1}
	{m,n}: m-n times

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
- `clear`
- `cmp file1 file2`: compare
- `cal` : calendar
- `echo "AaDCbd23" | tr "[A-Z]" "a-z"` : upper case to lower case, 
- `tr -c b-d =`: replace letters other than b-d by `=`
- `bc`: go to math
- `last` : list record for login
- `paste -sd '|||\n' test` : change every 4 lines to 1 line and use `|` to separate
- `wget -c` : continiously download
- `touch test.txt` 

