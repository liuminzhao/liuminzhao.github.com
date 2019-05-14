---
layout: post
title: "Animated Plots for Baby Name Initial"
description: ""
category: 
tags: [R, ggplot2, animated]
Time-stamp: "liuminzhao 2019/05/14"
---
{% include JB/setup %}

This is inspired by this [post](https://kieranhealy.org/blog/archives/2019/05/13/baby-name-animation/), however, in that post, the author was summarizing using `letter_count = n()` instead of `letter_count = sum(n)`, which did not consider the weights of occurance of each name; furthermore, I am more interested in the first letter in baby names by time. Therefore, here is my play around.

# Results

## Girls

<blockquote class="imgur-embed-pub" lang="en" data-id="a/YxGdlbL"><a href="//imgur.com/YxGdlbL"></a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script>

When you pause the gif at around 2000 - 2017, you can clear see the change of initial `A` comparing with that in 1800s. 

## Boys

<blockquote class="imgur-embed-pub" lang="en" data-id="a/Es5fsVr"><a href="//imgur.com/Es5fsVr"></a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script>

For boys, it's more interesting to see the peek used to be `J`, `R` and `W`, then by 2000s, `A, B` rises while `H, R` and `W` declines.


# Code

``` r
library(tidyverse)
library(babynames)
library(gganimate)

initial_gif = function(sexinterest){

  sexfull = ifelse(sexinterest == 'F', 'Girls', 'Boys')
  mytitle = str_c('Distribution of First Letters of U.S. ', sexfull, ' Names over Time')
    
  
  gif = babynames %>%
    filter(sex == sexinterest) %>%
    mutate(firstletter = stringr::str_sub(name, 1, 1)) %>%
    group_by(year, firstletter) %>%
    summarize(letter_count = sum(n)) %>%
    mutate(letter_prop = letter_count / sum(letter_count), 
           rank = min_rank(-letter_prop) * 1) %>%
    ungroup() %>% 
    ggplot(aes(x = firstletter,
               y = letter_prop,
               group = firstletter,
               fill = factor(firstletter),
               color = factor(firstletter))) +
    geom_col(alpha = 0.8) +
    scale_y_continuous(labels = scales::percent_format(accuracy = 1)) +
    guides(color = FALSE, fill = FALSE) +
    labs(title = mytitle,
         subtitle  = '{closest_state}',
         x = "", y = "Names Starting in letter",
         caption = "Data: US Social Security Administration. @liuminzhao") +
    theme(plot.title = element_text(size = rel(2)),
          plot.subtitle = element_text(size = rel(3)),
          plot.caption = element_text(size = rel(2)),
          axis.text.x = element_text(face = "bold", size = rel(3)),
          axis.text.y = element_text(size = rel(3)),
          axis.title.y = element_text(size = rel(2))) +
    transition_states(year, transition_length = 4, state_length = 1) +
    ease_aes('cubic-in-out')
  
  
  animate(gif, duration = 60, fps = 30,  width = 1200, height = 1000, end_pause = 30,
          renderer = gifski_renderer(str_c(sexfull, ".gif"))) 
  
  animate(gif, duration = 60, fps = 30,  width = 1200, height = 1000, end_pause = 30, 
          renderer = ffmpeg_renderer()) -> for_mp4
  
  anim_save(str_c(sexfull, ".mp4"), animation = for_mp4)

}
```