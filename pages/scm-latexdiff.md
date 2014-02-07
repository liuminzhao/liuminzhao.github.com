---
layout: page
title: "Scm Latexdiff"
description: ""
---
{% include JB/setup %}

===========
scm-latexdiff
===========

A command line tool to create diff pdf's from git and mercurial repos.
The script will automatically detect if the repo is git or hg. The
result is a pdf with the differences between the revisions, diff.pdf.

Usage:

	scm-latexdiff OLD:FILE NEW:FILE DIFF_DIR

where:

	OLD:    old revision id, local for non-commited
	NEW:    new revision id, local for non-commited
	FILE:   filename of the file you want to diff
	DIFF_DIR: diff file directory

Examples
========

for git

	scm-latexdiff 87213:draft/spam.tex 97123:draft/spam.tex draft

A sample of the `diff.pdf`:

![diff](http://i.imgur.com/hjLPUMg.png)

Notes
=====

I kept `diff.aux`, `diff.tex` files and added `DIFF_DIR` to allow troublesome when sometimes `Bibtex` does not work. Please run this script under root directory for the repo.

INSTALL
=======

The code is hosted on [github](https://github.com/liuminzhao/scm-latexdiff).

This tool uses distutils for installation. The following command installs
the tool on your machine:

	python setup.py install

To install to a non-standard directory tree (e.g. in your home directory) use
`--prefix`:

	python setup.py install --prefix=/home/spam/

Do remember to add `/home/spam/lib/python2.x/site-packages/` to your `PYTHONPATH` environment variable.
