---
title: "Example Data Exploration 
  Digging into the *gapminder* dataset"
author: "Stephen Chignell"
date: "September 18, 2018"
output:
  html_document:
    keep_md: true
---



## Overview
The following sections will demonstrate exploratory data analysis in R. We will start by familiziarizing ourselves with the *gapminder* dataset, and then produce a few plots to visualize interesting patterns in the data.


### Load the dataset

```r
library(gapminder)
```

```
## Warning: package 'gapminder' was built under R version 3.5.1
```

#### Explore its structure
The "str" function provides detailed information on the type and composition of the dataset:

```r
str(gapminder)
```

```
## Classes 'tbl_df', 'tbl' and 'data.frame':	1704 obs. of  6 variables:
##  $ country  : Factor w/ 142 levels "Afghanistan",..: 1 1 1 1 1 1 1 1 1 1 ...
##  $ continent: Factor w/ 5 levels "Africa","Americas",..: 3 3 3 3 3 3 3 3 3 3 ...
##  $ year     : int  1952 1957 1962 1967 1972 1977 1982 1987 1992 1997 ...
##  $ lifeExp  : num  28.8 30.3 32 34 36.1 ...
##  $ pop      : int  8425333 9240934 10267083 11537966 13079460 14880372 12881816 13867957 16317921 22227415 ...
##  $ gdpPercap: num  779 821 853 836 740 ...
```
We can see that the dataset has 6 fields (or "variables"), with 1704 entries (or "observations"). Some of these contain numerical data and others contain text data.


#### Summarize the data
The "summary" function provides basic descriptive statistics of each field:


```r
summary(gapminder)
```

```
##         country        continent        year         lifeExp     
##  Afghanistan:  12   Africa  :624   Min.   :1952   Min.   :23.60  
##  Albania    :  12   Americas:300   1st Qu.:1966   1st Qu.:48.20  
##  Algeria    :  12   Asia    :396   Median :1980   Median :60.71  
##  Angola     :  12   Europe  :360   Mean   :1980   Mean   :59.47  
##  Argentina  :  12   Oceania : 24   3rd Qu.:1993   3rd Qu.:70.85  
##  Australia  :  12                  Max.   :2007   Max.   :82.60  
##  (Other)    :1632                                                
##       pop              gdpPercap       
##  Min.   :6.001e+04   Min.   :   241.2  
##  1st Qu.:2.794e+06   1st Qu.:  1202.1  
##  Median :7.024e+06   Median :  3531.8  
##  Mean   :2.960e+07   Mean   :  7215.3  
##  3rd Qu.:1.959e+07   3rd Qu.:  9325.5  
##  Max.   :1.319e+09   Max.   :113523.1  
## 
```
Here we see that we are working with demographic information from a variety of countries ranging from the years 1952-2007. Already we can identify some interesting information. For example,

- Life expectany ranges from 23.60 to 82.60 years
- Population ranges from 60,010 to 1,319,000,000



```r
hist(gapminder$pop)
```

![](hw01_gapminder-exploration_files/figure-html/unnamed-chunk-4-1.png)<!-- -->


Let's find which countries and years these values are associated with. 


```r
head(gapminder)
```

```
## # A tibble: 6 x 6
##   country     continent  year lifeExp      pop gdpPercap
##   <fct>       <fct>     <int>   <dbl>    <int>     <dbl>
## 1 Afghanistan Asia       1952    28.8  8425333      779.
## 2 Afghanistan Asia       1957    30.3  9240934      821.
## 3 Afghanistan Asia       1962    32.0 10267083      853.
## 4 Afghanistan Asia       1967    34.0 11537966      836.
## 5 Afghanistan Asia       1972    36.1 13079460      740.
## 6 Afghanistan Asia       1977    38.4 14880372      786.
```


### Plot the data
Let's use the "plot" function in base R to see how population has changed over time.
We can also provide basic labels with "ylab", "xlab", and "main".

```r
plot(gapminder$year,gapminder$pop, 
     ylab = "Population (scientific notation", 
     xlab ="Year",
     main = "Population through time")
```

![](hw01_gapminder-exploration_files/figure-html/unnamed-chunk-6-1.png)<!-- -->
We see that population has been increasing, but there are two trends that are far steeper and greater than the rest of the data. 

























## R Markdown

This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and MS Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

When you click the **Knit** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:


```r
summary(cars)
```

```
##      speed           dist       
##  Min.   : 4.0   Min.   :  2.00  
##  1st Qu.:12.0   1st Qu.: 26.00  
##  Median :15.0   Median : 36.00  
##  Mean   :15.4   Mean   : 42.98  
##  3rd Qu.:19.0   3rd Qu.: 56.00  
##  Max.   :25.0   Max.   :120.00
```

## Including Plots

You can also embed plots, for example:

![](hw01_gapminder-exploration_files/figure-html/pressure-1.png)<!-- -->

Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.
