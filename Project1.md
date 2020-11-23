---
title: "Reproducible Research: Peer Assessment 1"
output: 
  html_document:
    keep_md: true
---

## Loading R library

```r
library("dplyr")
```

```
## 
## Attaching package: 'dplyr'
```

```
## The following objects are masked from 'package:stats':
## 
##     filter, lag
```

```
## The following objects are masked from 'package:base':
## 
##     intersect, setdiff, setequal, union
```

```r
library("ggplot2")
```

## Loading and preprocessing the data

```r
tPath <- "D:/00-PDrive/MyStudy/01-Course/00-Coursera/2-DSFusingR/5-Reproducible/Project1"
setwd(tPath)
master <- as.character(unzip("repdata_data_activity.zip", list = TRUE)$Name)
Dat <- read.csv(unz("repdata_data_activity.zip", "activity.csv"), header = TRUE, sep = ",") 
dim(Dat)
```

```
## [1] 17568     3
```

```r
head(Dat)
```

```
##   steps       date interval
## 1    NA 2012-10-01        0
## 2    NA 2012-10-01        5
## 3    NA 2012-10-01       10
## 4    NA 2012-10-01       15
## 5    NA 2012-10-01       20
## 6    NA 2012-10-01       25
```

```r
Dat$date <- as.Date(Dat$date, "%Y-%m-%d")
str(Dat)
```

```
## 'data.frame':	17568 obs. of  3 variables:
##  $ steps   : int  NA NA NA NA NA NA NA NA NA NA ...
##  $ date    : Date, format: "2012-10-01" "2012-10-01" ...
##  $ interval: int  0 5 10 15 20 25 30 35 40 45 ...
```
## What is mean total number of steps taken per day?

- Aggregation total steps according to day

```r
totSteps <- Dat %>%
    group_by(date) %>%
    summarise_at(vars(steps), list(totSteps = sum), na.rm = TRUE)
totStepsbyDay <- as.data.frame(totSteps)
head(totStepsbyDay)
```

```
##         date totSteps
## 1 2012-10-01        0
## 2 2012-10-02      126
## 3 2012-10-03    11352
## 4 2012-10-04    12116
## 5 2012-10-05    13294
## 6 2012-10-06    15420
```
- Draw a graph to show the total number of steps for each day

```r
g <- ggplot(data = totStepsbyDay, aes(x= date, y = totSteps))
g <- g + geom_bar(stat = "identity", color="blue", fill="steelblue")
g + ylab("Total Steps") + xlab("") 
```

![](Project1_files/figure-html/totGraph-1.png)<!-- -->

- Histogram of the total number of steps taken each day

```r
hist(totStepsbyDay$totSteps, xlab = "Total Steps per Dat", main = "Histogram of the total number of steps taken each day")
```

![](Project1_files/figure-html/unnamed-chunk-2-1.png)<!-- -->

- Mean and median of the total number of steps taken per day:  9354 and 10395


```r
summary(totStepsbyDay$totSteps)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##       0    6778   10395    9354   12811   21194
```

## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
