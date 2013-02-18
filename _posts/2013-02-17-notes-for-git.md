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
	
	
