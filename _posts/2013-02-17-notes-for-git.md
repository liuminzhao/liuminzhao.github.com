---
layout: post
title: "notes for git"
description: ""
category:
tags: [git]
---
{% include JB/setup %}

# Merge #

	git merge old new

or

    git checkout master
	git merge branch

# rebase #

similar to `merge`, but put forward and forma a linear relation

	git rebase master (move bugFix to master branch)
	then
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

# Push to multiple repo #

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

## show remote in status ##

Sometimes it does not show remote branch on status bar, it means you do not have the default remote for current branch. Just add the following:

	[branch "master"]
		remote = origin
