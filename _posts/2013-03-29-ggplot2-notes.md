---
layout: post
title: "ggplot2 notes"
description: ""
category: 
tags: [ggplot2]
---
{% include JB/setup %}

GGPLOT2 Notes
==========

# Basic #

Two main functions:

- `qplot()`  : quick plot
- `ggplot()` 

Usage:

## Histogram ##

    qplot(x,main = "")
	
## Scatterplot ##

    qplot(x, y, log = "xy", color=..)
	
## Boxplot ##

    qplot(x, y)
	qplot(x, y, geom = "boxplot")
	
# Geom #	
	
	geom = "bar"
	"histogram", binwidth = 0.1
	jitter
	 = c("point", "smooth"), method = "lm"
	 dotplot
	 point
	
# Alpha #	
	
	alpha = I(1/4)
	
# Shape #
	
	shape = 1, 2, or '.'
	
# Size #
	
# Fill #
	
# Facet #

    qplot(data=myData,x=BM,y=var1,log="xy",color=Tribe,facets = Hab~Tribe)
	qplot(data=myData,x=BM,y=var1,log="xy",color=Tribe,facets = ~Tribe)

# Add #

    myGG<- myGG + stat_smooth(method="lm")
	+layer(geom="point")
	+geom_point(color = "blue")
	+geom_line()
	+ geom_abline(intercept = a, slope = b)
	
	
# Save #

    ggsave("LIBMFacetsWithTrend.jpg")
