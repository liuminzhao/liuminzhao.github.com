---
layout: post
title: "browser history"
description: ""
category: 
tags: [sqlite, url, R, barplot, privacy, db]
Time-stamp: "liuminzhao 2021/01/20"
---
{% include JB/setup %}

This post is insipred by the uploader [偶尔有点小迷糊](https://space.bilibili.com/39665558?from=search&seid=7521790958789947383), however his post was removed for some reason in Bilibili. In his video, he introduced how to use python to get your browser history and make a pie chart of it. I borrowed his idea here and use R code to explore what I browse most via Bar chart. 

# R Package Required

```r
library(DBI)
library(dplyr)
library(urltools)
library(ggplot2)
```

# history file

The chrome history file in Windows is **SQLite** so we can use package `DBI` to connect and read. 

```r
con <- dbConnect(RSQLite::SQLite(), "C:/Users/liumi/AppData/Local/Google/Chrome/User Data/Default/History")
```

You may replace with your user name. 

# Some basic SQLITE command: 

```r
dbListTables(con)

dbListFields(con, "urls")
```

# the URL

```r
urls = dbReadTable(con, "urls") #Read the URL

domain = url_parse(urls$url)$domain # parse the url to get the main domain

domaint = tibble(domain, weights = urls$visit_count) # REMEMBER TO GET WEIGHTS

# get count

domain_count = domaint %>% 
  count(domain, wt=weights) %>% 
  arrange(desc(n)) 

# get top n=10
domain_count_top = domain_count %>% 
  top_n(10) %>% 
  mutate(prop = n / sum(n)*100) %>%
  mutate(ypos = prop/2, rank = row_number(), propc = scales::label_percent()(prop/100) )

# site list
sitelist = domain_count_top$domain
```

# Plot

```r
# Basic bar chart
ggplot(domain_count_top, aes(x=rank, y=prop, fill=domain)) +
  geom_tile(aes(y = ypos, height = prop, fill = domain), width = 0.9) +
  geom_text(aes(label = propc), hjust = "right", nudge_y = .01, colour = "grey30") +
  coord_flip(clip="off") +
  scale_x_reverse("", labels=sitelist,  breaks = 1:10) +
  theme(panel.grid.major.y=element_blank(),
        panel.grid.minor.x=element_blank(), 
        legend.position = "none",
        axis.text.x = element_blank(), 
        axis.title.x = element_blank()
        )

# disconnect DB
dbDisconnect(con)
```

# Result

<blockquote class="imgur-embed-pub" lang="en" data-id="a/xVoyjBS" data-context="false" ><a href="//imgur.com/a/xVoyjBS"></a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script>

Please note those percentages are based on the top n (10), and you may display the percentages based on the total history. 