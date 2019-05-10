---
title: "Animated Bar Plot for NBA Standing"
category: null
description: ''
layout: post
tags:
- R
- ggplot2
- nba
Time-stamp: ' '
---
{% include JB/setup %}

Inspired by the viral animated bar plot, I plan to implement the idea on
NBA standing so that we can have an idea how the teams behavior through
out the whole season. special thanks to the two blogs by
[Michael](https://michaeltoth.me/how-to-create-a-bar-chart-race-in-r-mapping-united-states-city-population-1790-2010.html)
and
[Abdul](https://datascienceplus.com/how-to-build-animated-bar-plots-using-r/)
for instructions how to make animated bar plots using **R**,
**ggplot2**, and package **gganimate**.

Data Preparation
----------------

First we need to load three great R packages:

``` r
library(tidyverse)
library(nbastatR)
library(gganimate)
```

Package *tidyverse* is for data manipulation;
[nbastatR](https://github.com/abresler/nbastatR) is a great package
using NBA Stats API Wrapper; *gganimate* is to make animated plots.

### Get Team Color

Next step, I am going to use the `nba_teams()` function to get the team
information along with their main color.

``` r
nba_team = nba_teams()
nba_team %>% 
  filter(isNonNBATeam == 0) %>% 
  select(cityTeam, hexColor1) -> teamcolor
head(teamcolor)
```

    ## # A tibble: 6 x 2
    ##   cityTeam    hexColor1
    ##   <chr>       <chr>    
    ## 1 Washington  #002B5C  
    ## 2 Utah        #002B5C  
    ## 3 Toronto     #CE1141  
    ## 4 San Antonio #C4CED4  
    ## 5 Sacramento  #5A2D81  
    ## 6 Portland    #E03A3E

Then make it a named list:

``` r
colorlist = as.character(teamcolor$hexColor1)
teamname2 = teamcolor$cityTeam
teamname2 = replace(teamname2, teamname2=='Los Angeles', 'L.A. Lakers')
teamname2 = replace(teamname2, teamname2=='LA', 'LA Clippers')
names(colorlist) = teamname2
colorlist
```

    ##    Washington          Utah       Toronto   San Antonio    Sacramento 
    ##     "#002B5C"     "#002B5C"     "#CE1141"     "#C4CED4"     "#5A2D81" 
    ##      Portland       Phoenix  Philadelphia       Orlando Oklahoma City 
    ##     "#E03A3E"     "#E56020"     "#006BB6"     "#0077C0"     "#007AC1" 
    ##      New York   New Orleans     Minnesota     Milwaukee         Miami 
    ##     "#F58426"     "#0C2340"     "#0C2340"     "#00471B"     "#98002E" 
    ##       Memphis   L.A. Lakers   LA Clippers       Indiana       Houston 
    ##     "#6189B9"     "#552583"     "#ED174C"     "#FDBB30"     "#CE1141" 
    ##  Golden State       Detroit        Denver        Dallas     Cleveland 
    ##     "#FDB927"     "#006BB6"     "#418FDE"     "#00538C"     "#6F263D" 
    ##       Chicago     Charlotte      Brooklyn        Boston       Atlanta 
    ##     "#CE1141"     "#00788C"     "#000000"     "#007A33"     "#E03A3E"

### Get Standing by Day

Use the function `day_scores` to pull the standing information by day
and wrap up as function:

``` r
pull_east_standing = function(date){
  days_scores(game_dates = date, 
              include_standings = T, return_message = F)
  
  dataScoreEastConfStandingsByDayNBA
}

pull_west_standing = function(date){
  days_scores(game_dates = date, 
              include_standings = T, return_message = F)
  
  dataScoreWestConfStandingsByDayNBA
}
```

## Wrap up and Plot


``` r
gif_standing = function(seasonyear, conf){
  
  # get season info start date and end date
  season = seasons_schedule(seasons = seasonyear)
  datelist = unique(season %>% select(dateGame))
  
  # get season standing by day
  if (conf == 'East') {
    standing_day = datelist %>% map_dfr(pull_east_standing)
  } else if (conf == 'West') {
    standing_day = datelist %>% map_dfr(pull_west_standing)
  }
  
  # add rank per day
  standing_day %>% 
    group_by(dateGame) %>% 
    mutate(rank = row_number(),
           wl = str_c(wins, losses, sep = '-')) %>% 
    ungroup() -> final
  
  # title
  mytitle = str_c(conf, ' Conference Standing, ', seasonyear)
  
  # gif
  gif = final %>%
    ggplot(aes(x = rank,y = pctWins, group = slugTeam)) +
    geom_tile(aes(y = pctWins/2, height = pctWins, fill = slugTeam), width = 0.9) +
    geom_text(aes(label = slugTeam), hjust = "right", colour = "black", fontface = "bold", nudge_y = -0.02) +
    geom_text(aes(label = wl), hjust = "left", nudge_y = .01, colour = "grey30") +
    coord_flip(clip="off") +
    scale_fill_manual(name = 'Team', values = colorlist) +
    scale_x_reverse("",  breaks = 1:15) +
    scale_y_continuous(limits = c(0, 1), "Win Rate") +
    geom_vline(xintercept = 8.5) +
    #hrbrthemes::theme_ipsum(plot_title_size = 32, subtitle_size = 24, caption_size = 20, base_size = 20) +
    theme(panel.grid.major.y=element_blank(),
          panel.grid.minor.x=element_blank()) +
    # gganimate code to transition by date:
    transition_time(dateGame) +
    ease_aes('cubic-in-out') +
    labs(title=mytitle,
         subtitle='Date: {round(frame_time,0)}',
         caption='Source: NBA Stat 
         Minzhao Liu')

}
```

## Make Gif and MP4

``` r
gif_2019e = gif_standing(2019, 'East')
gif_2019w = gif_standing(2019, 'West')

animate(gif_2019e, duration = 60, fps = 20,  width = 1200, height = 1000, end_pause = 30,
        renderer = gifski_renderer("gganim_2019e.gif")) 


animate(gif_2019w, duration = 60, fps = 30,  width = 1200, height = 1000, 
        end_pause = 30, renderer = gifski_renderer("gganim_2019w.gif")) 

# For MP4

animate(gif_2019w, duration = 60, fps = 30,  width = 1200, height = 1000, end_pause = 30, 
        renderer = ffmpeg_renderer()) -> for_mp4

anim_save("animation_2019w.mp4", animation = for_mp4 )
```

Results
---------------

<blockquote class="imgur-embed-pub" lang="en" data-id="Iaztd8b"><a href="//imgur.com/Iaztd8b">View post on imgur.com</a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script>


<figure class="video_container">
  <iframe src="https://www.youtube.com/embed/r41AWlKdNy0" frameborder="0" allowfullscreen="true"> </iframe>
</figure>
