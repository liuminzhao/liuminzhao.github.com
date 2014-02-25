---
layout: post
title: "notes dplyr"
description: ""
category:
tags: [R]
Time-stamp: "liuminzhao 02/25/2014 16:15:01"
---
{% include JB/setup %}

Notes for dplyr
===============

<http://cran.r-project.org/web/packages/dplyr/vignettes/introduction.html>

# Basic verbs

## `filter()`

subset of dataset

	filter(dat, month == 1 | month == 2)

## `arrange()`

sort the dataset

	arrange(dat, year, month, date)

## `select()`

select columns

	select(dat, col1, col2)
	select(dat, col1:col5)
	select(dat, -(col1:col5))

new feature for ddply 0.1.2:

	select(df, starts_with("xyz_"))
	select(df, contains("xyz_"))
	select(df, ends_with("xyz_"))
	select(df, matches("xyz.*"))
	select(df, num_range(x1:xN)


## `mutate()`

add new columns

	mutate(dat, newvar = col1 - col2, newvar2 = mean(x))

## `summarise()`

collapse data to a single row

	summarise(dat, meanx = mean(x))

# Grouped operations

	bycol1 = group_by(dat, col1)
	newsummary = summarise(bycol1,
		count = n(),
		meanx = mean(x))
	newsummary = filter(newsummary, count > 20, meanx < 200)

plot:

	ggplot(newsummary, aes(x, y)) + geom_point(aes(y),) + geom_smooth() + scale_size_area()

can use *aggregate function* like `min`, `max`, `sd`, `IQR`

	n()
	count_distinct(x)
	first(x)
	last(x)
	nth(x, n)

can group by couples of levels

	group_by(dat, year, month, date)

# Window functions

## ranking and ordering

	x = c(1, 1, 2,2,2)

	row_number(): 1,2,3,4,5; rank
	min_rank(): 1,1, 3,3,3
	dense_rank(): 1,1,2,2,2
	cume_dist(): 0.4, 0.4, 1, 1, 1; proportion of values less than or equal to the current value
	percent_rank(): 0, 0, 0.5, 0.5, 0.5;  percentage of the rank
	ntile():  divides the data up into n evenly sized buckets
	desc() : to rank from highest to lowest.

## offsets

	lead(): next; 2,3,4,5,NA
	lag(): previous, NA, 1,2,3,4

## other three families are variations on familiar aggregate functions

	cumsum()
	cummin()
	cummax()
	cumall()
	cumany()
	cummean()

example:

all record for a player after they have played 150 games

	filter(players, cumany(G > 150))

# `order_by`

use another variable to order

	right <- mutate(scrambled, running = order_by(year, cumsum(value)))
