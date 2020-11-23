---
title: "Reproducible Research: Peer Assessment 1"
output: 
  html_document:
    keep_md: true
---


## Loading and preprocessing the data

```r
tPath <- "D:/00-OneDrive/GitHub/RepData_PeerAssessment1"
setwd(tPath)
master <- as.character(unzip("activity.zip", list = TRUE)$Name)
Dat <- read.csv(unz("activity.zip", "activity.csv"), header = TRUE, sep = ",") 
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



## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
