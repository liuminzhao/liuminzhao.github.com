---
layout: post
title: "notes python wrangling"
description: ""
category:
tags: []
Time-stamp: "liuminzhao 01/02/2014 10:08:29"
---
{% include JB/setup %}

reference: <http://nbviewer.ipython.org/github/cs109/content/blob/master/lec_04_wrangling.ipynb>

# basic workflow

1. Build a DataFrame from the data (ideally, put all data in this object)
2. Clean the DataFrame. It should have the following properties:
   - Each row describes a single object
   - Each column describes a property of that object
   - Columns are numeric whenever appropriate
   - Columns contain atomic properties that cannot be further decomposed
3. Explore global properties. Use histograms, scatter plots, and aggregation functions to summarize the data.
4. Explore group properties. Use groupby and small multiples to compare subsets of the data.

# build dataframe

	names = ['imdbID', 'title', 'year', 'score', 'votes', 'runtime', 'genres']
	data = pd.read_csv('imdb_top_10000.txt', delimiter='\t', names=names).dropna()
	print "Number of rows: %i" % data.shape[0]
	data.head()  # print the first 5 rows

# clean

	clean_runtime = [float(r.split(' ')[0]) for r in data.runtime]
	data['runtime'] = clean_runtime
	data.head()

## splitting

	#determine the unique genres
	genres = set()
	for m in data.genres:
		genres.update(g for g in m.split('|'))
	genres = sorted(genres)

    #make a column for each genre
	for genre in genres:
		data[genre] = [genre in movie.split('|') for movie in data.genres]

	data.head()

# explore

## call `describe`

	data[['score', 'runtime', 'year', 'votes']].describe()

# basic plots

	plt.hist(data.year, bins=np.arange(1950, 2013), color='#cccccc')
	plt.xlabel("Release Year")
	remove_border()
