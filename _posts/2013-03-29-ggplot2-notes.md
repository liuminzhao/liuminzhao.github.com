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
	ggplot(data, aes(x)) + geom_histogram(binwidth = , color = , fill = )

## Scatterplot ##

    qplot(x, y, log = "xy", color=..)
	ggplot(data, aes(x = , y = , color = )) + geom_point()

## Boxplot ##

    qplot(x, y)
	qplot(x, y, geom = "boxplot")
	ggplot(data, aes(factor(race), y)) + geom_boxplot()

## Line ##

    ggplot(data, aes(x, y)) + geom_line()

Line by group

	ggplot(dat, aes(x = date, y = target, color = factor(account_id), group = account_id)) + geom_point() + geom_line()

## Density ##

    ggplot(data, aes(y)) + geom_density(fill = 'blue')
	 + geom_line(stat = "density")

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

# Label #

	ggplot(...) + ylab('mylabel')
	bp + scale_x_discrete(breaks=c("ctrl", "trt1", "trt2"), labels=c("Control", "Treat 1", "Treat 2"))

# Save #

    ggsave("LIBMFacetsWithTrend.jpg", width = 6, height = 4)

# ggplot2 #

<https://speakerdeck.com/karthik/introduction-to-ggplot2>

never use `qplot`

    ggplot(data, aes(x = x, y = y)) + geom_line()

# aes #

    aes(shape = x)

# density #

    geom_density()
	geom_line(stat = "density")

## smooth ##

    + geom_smooth(method = "lm")


# Arrange #

    library(gridExtra)
	sidebysideplot <- grid.arrange(plot1, plot2, ncol=2)
