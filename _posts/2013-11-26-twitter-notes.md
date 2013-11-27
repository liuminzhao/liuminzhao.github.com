---
layout: post
title: "twitteR notes"
description: ""
category:
tags: []
Time-stamp: "liuminzhao 11/26/2013 22:55:11"
---
{% include JB/setup %}

# Initial #

go to `https://twitter.com/apps/new`

	library(ROauth)
	library(twitteR)
	cred <- OAuthFactory$new(consumerKey='secret',
	consumerSecret='secret',
	requestURL='https://api.twitter.com/oauth/request_token',
	accessURL='http://api.twitter.com/oauth/access_token',
	authURL='http://api.twitter.com/oauth/authorize')
	cred$handshake()
	save(cred, file="twitter-authentication.Rdata")
	registerTwitterOAuth(cred)

# Use #

	cranTweets <- userTimeline('liuminzhao', n = 100)
	searchTwitter('#fdsf', n = 50)
	getUser('liuminzhao')

	# Convert the list to a data frame
	tweets <- twListToDF(tweets)
	tweets <- unique(tweets)

# With Data Mining #

	library('wordcloud')
	library('tm')
	r_stats<- searchTwitter("#Rstats", n=1500, cainfo="cacert.pem")
	r_stats_text <- sapply(r_stats, function(x) x$getText())
	r_stats_text_corpus <- Corpus(VectorSource(r_stats_text))
	r_stats_text_corpus <- tm_map(r_stats_text_corpus, tolower)
	r_stats_text_corpus <- tm_map(r_stats_text_corpus, removePunctuation)
	r_stats_text_corpus <- tm_map(r_stats_text_corpus, function(x)removeWords(x,stopwords()))
	wordcloud(r_stats_text_corpus)

Unicode:

	tm_map(yourCorpus, function(x) iconv(x, to='UTF-8-MAC', sub='byte'))

# Limit #

	rate.limit <- getCurRateLimitInfo()

# Reference #

1. <http://davetang.org/muse/2013/04/06/using-the-r_twitter-package/>
2. <https://sites.google.com/site/miningtwitter/references>
3. <http://gettinggeneticsdone.blogspot.com/2012/07/plotting-frequency-of-twitter-hashtag.html>
