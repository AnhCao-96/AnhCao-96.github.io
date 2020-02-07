---
title: "R language: English Premier League Soccer Standings"
date: 2020-02-07
tags: [R, Tidyverse, Dplyr, Lubridate, EPL, Soccer]
header:
  image: "/images/EPL/EPL.jpg"
excerpt: "R programing, EPL Standings, Soccer"
---
# INTRODUCTION

The English Premier League (EPL) is a major soccer league in Great Britain consisting of 20 teams.  The season begins in August and concludes in May with each team playing each other team exactly twice (home and away).  Each team plays 38 games in a season while the total number of games is 380.  A team receives 3 points for a win and if the game is tied, both teams receive 1 point; no points are awarded for a loss.

This is an individual project to develop a function with the inputs of *date* and *season* that returns the league standings for the date ad season specified (e.g. '04/25/2018', '2017/18').

The data sets were found [here](http://www.football-data.co.uk/englandm.php) under the heading *Premier League*.

You can find the full project description and the code [here](https://github.com/AnhCao-96/EPL-Standings).

# FUNCTIONS AND CODE COMMENTS

## Data Preparation
Load the libraries and create a list of the links to load the full data sets directly from the website:
```r
library(tidyverse)
library(lubridate)
library(dplyr)
library(scales)

links = list(
  "2019/20" = "http://www.football-data.co.uk/mmz4281/1920/E0.csv",
  "2018/19" = "http://www.football-data.co.uk/mmz4281/1819/E0.csv",
  "2017/18" = "http://www.football-data.co.uk/mmz4281/1718/E0.csv"
)
```
Create a function to load the desired dataset that indicates the data type of each needed columns. Read the dataset from the link list based on the season input with the date in 'dmy' form. Check on not null dates. Keep the records having happened before the date input (within the season input only).
```r
load_data <- function(date = NULL, season) {
  col_types = cols(
    HomeTeam = col_character(),
    AwayTeam = col_character(),
    FTHG = col_integer(),
    FTAG = col_integer(),
    FTR = col_character()
  )
  df <- read_csv(url(links[[season]]), col_types = col_types) %>%
      select(Date, HomeTeam, AwayTeam, FTHG, FTAG, FTR) %>%
      mutate(Date = dmy(Date))
    if (!is.null(date)) {
      return(df %>% filter(Date <= mdy(date)))
    }
    return(df)
  }
```
