---
layout: post
title: "notes python scraping"
description: ""
category:
tags: []
Time-stamp: "liuminzhao 03/08/2014 13:38:50"
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


## with header (twitch)

	headers = {'Accept': 'application/vnd.twitchtv.v2+json'}
	hs_url = 'https://api.twitch.tv/kraken/streams?game=Hearthstone%3A%20Heroes%20of%20Warcraft'
	r = requests.get(hs_url, headers = headers)


# get soup

	from urllib2 import urlopen
	html = urlopen(url).read()
	soup = BeautifulSoup(html)


# Using bs4 (method)

	bs = BeautifulSoup(r.text)
	for movie in bs.findAll('td', 'title'):
		title = movie.find('a').contents[0]
		genres = movie.find('span', 'genre').findAll('a')
		genres = [g.contents[0] for g in genres]
		runtime = movie.find('span', 'runtime').contents[0]
		rating = movie.find('span', 'value').contents[0]
		print title, genres, runtime, rating


## `soup.find_all`

can find tag name, attribute, text, and string

	soup.find_all('b')
	find_all(re.compile("^b"))
	find_all("title")
	find_all("p", "title")
	find_all(id = "jlj")

## find all url

	for link in soup.find_all('a'):
		print(link.get('href'))

## All text

	print(soup.get_text())

# json

	import json
	r = requests.get(hs_url, headers = headers)
	rjson = r.json()['streams']
