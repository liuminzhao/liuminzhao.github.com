---
layout: post
title: "notes python scraping"
description: ""
category:
tags: []
Time-stamp: "liuminzhao 01/02/2014 09:46:56"
---
{% include JB/setup %}

<http://nbviewer.ipython.org/github/cs109/content/blob/master/lec_04_scraping.ipynb>

# get request

	import requests
	from pattern import web
	from bs4 import BeautifulSoup

	url = 'http://www.imdb.com/search/title?sort=num_votes,desc&start=1&title_type=feature&year=1950,2012'
	r = requests.get(url)
	print r.url

# Using bs4

	bs = BeautifulSoup(r.text)
	for movie in bs.findAll('td', 'title'):
		title = movie.find('a').contents[0]
		genres = movie.find('span', 'genre').findAll('a')
		genres = [g.contents[0] for g in genres]
		runtime = movie.find('span', 'runtime').contents[0]
		rating = movie.find('span', 'value').contents[0]
		print title, genres, runtime, rating
