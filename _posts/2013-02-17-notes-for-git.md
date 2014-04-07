---
layout: post
title: "notes for git"
description: ""
category:
tags: [git]
Time-stamp: "liuminzhao 03/30/2014 10:37:37"
---
{% include JB/setup %}

# Merge #

	git merge old new

or

    git checkout master
	git merge branch

usually just fast forward the [HEAD](http://www.slideshare.net/littlebtc/git-5528339).

# rebase #

similar to `merge`, but put forward and form a linear relation

	git rebase master (move bugFix to master branch)

then

	git checkout master
	git merge bugFix

because after rebase, we can fast-forward merge.

or

	git rebase bugFix (move master head to bugFix)

# Reverse #

1. `reset`
2. `revert`

	git reset HEAD~1 # go back to previous HEAD as never happened, work nice with local
	git revert HEAD # make a new commit, but record the change back to HEAD


# Checkout #

Checkout specific file from other branch

    git checkout master -- file

# Troublesome #

X11 error when `git push`:

change `~/.ssh/config`:

	ForwardX11 no

# Push

## Push branch to remote

	git push -u origin mynewfeature

## Push to multiple repo #

add to `.git/config`:

	[remote "all"]
    url=ssh://user@server/repos/g0.git
    url=ssh://user@server/repos/g1.git

then `git push all master`.

# Emacs/Magit #

change magit diff default color

	(eval-after-load 'magit
	'(progn
    (set-face-foreground 'magit-diff-add "green3")
    (set-face-foreground 'magit-diff-del "red3")
    (when (not window-system)
    (set-face-background 'magit-item-highlight "black"))))

	k: reverts file; drop them

## show remote in status ##

Sometimes it does not show remote branch on status bar, it means you do not have the default remote for current branch. Just add the following:

	[branch "master"]
		remote = origin

## Reference ##

<http://daemianmack.com/magit-cheatsheet.html#sec-8>


# Pull #

Pull = fetch + merge

## pull remote branch

	git fetch origin
	git checkout --track origin/daves_branch

# branch #

A new branch with new history:

	git checkout --orphan NEW_BRANCH_NAME_HERE

# Mercurial #

## Convert Mercurial project to Git ##

<http://stackoverflow.com/questions/16037787/convert-mercurial-project-to-git>

	cd ~
	git clone git://repo.or.cz/fast-export.git
	git init git_repo
	cd git_repo
	~/fast-export/hg-fast-export.sh -r /path/to/old/mercurial_repo
	git checkout HEAD
