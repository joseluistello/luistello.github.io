---
layout: post
title: "Forecasting Mexico"
description: "An introduction to forecasting modeling"
output: html_document
date: 2021-05-22 19:50:00 -0400
category: r
tags: [data analysis, forecasting, r]
comments: true
---


## What Is Per Capita GDP? 

**Per capita gross domestic product (GDP)** is a metric that breaks down a country’s economic output per person and is calculated by dividing the GDP of a country by its population.

In this project, I'm going to visualize Mexico GDPPC growth and **forecasting GDPPC for the next 3 and 6 years.**

I’ll use the **fpp3** package. This package it’s created by **Rob J Hyndman and George Athanasopoulos.**

You can install the stable version from CRAN.

``` r
install.packages(‘fpp3’, dependencies = TRUE)
```

You can install the development version from Github

``` r
remotes::install\_github(“robjhyndman/fpp3-package”)
```

So, load the package.

``` r
library(fpp3)
```


### Manipulating data

By default, we have a data set from global economy (thanks to fpp3)

This data set contains 9 variables:

> Country, Code, Year, GDP, Growth, CPI, Imports, Exports, Population.

#### We only need GDPPC and Population. So, lets begin.

I'm going to start with dplyr and create a new column. This code creates a new frame that we are going to use across the project.

``` r
percapita <- global_economy %>%
  mutate(GDP_per_capita = GDP / Population)
```

Then, we make a pipeline to filter Mexico from column Country and plot the growth.

``` r
percapita %>%
  filter(Country == "Mexico",) %>%
  autoplot(GDP_per_capita) +
  labs(y = "Pesos",
       x = "Years",
       title = "Ingresos per capita for Mexico")
```

![](/images/chunk%201.png)<!-- -->

**Now we can make the forecasting model**

``` r
TSLM(GDP_per_capita ~ trend())
```

    ## <TSLM model definition>

``` r
fit <- percapita %>%
  model(trend_model = TSLM(GDP_per_capita ~ trend()))
```

    ## Warning: 7 errors (1 unique) encountered for trend_model
    ## [7] 0 (non-NA) cases


**We can see the values of fit just by writing fit.**

``` r
fit
```

    ## # A mable: 263 x 2
    ## # Key:     Country [263]
    ##    Country             trend_model
    ##    <fct>                   <model>
    ##  1 Afghanistan              <TSLM>
    ##  2 Albania                  <TSLM>
    ##  3 Algeria                  <TSLM>
    ##  4 American Samoa           <TSLM>
    ##  5 Andorra                  <TSLM>
    ##  6 Angola                   <TSLM>
    ##  7 Antigua and Barbuda      <TSLM>
    ##  8 Arab World               <TSLM>
    ##  9 Argentina                <TSLM>
    ## 10 Armenia                  <TSLM>
    ## # ... with 253 more rows


### Adding time by 3 years


``` r
fit %>% forecast(h = "3 years")
```

    ## # A fable: 789 x 5 [1Y]
    ## # Key:     Country, .model [263]
    ##    Country        .model       Year   GDP_per_capita  .mean
    ##    <fct>          <chr>       <dbl>           <dist>  <dbl>
    ##  1 Afghanistan    trend_model  2018     N(526, 9653)   526.
    ##  2 Afghanistan    trend_model  2019     N(534, 9689)   534.
    ##  3 Afghanistan    trend_model  2020     N(542, 9727)   542.
    ##  4 Albania        trend_model  2018  N(4716, 476419)  4716.
    ##  5 Albania        trend_model  2019  N(4867, 481086)  4867.
    ##  6 Albania        trend_model  2020  N(5018, 486012)  5018.
    ##  7 Algeria        trend_model  2018  N(4410, 643094)  4410.
    ##  8 Algeria        trend_model  2019  N(4489, 645311)  4489.
    ##  9 Algeria        trend_model  2020  N(4568, 647602)  4568.
    ## 10 American Samoa trend_model  2018 N(12491, 652926) 12491.
    ## # ... with 779 more rows

``` r
fit %>%
  forecast(h = "3 years") %>%
  filter(Country == "Mexico") %>%
  autoplot(percapita) +
  labs(y = "$Pesos", title = "Ingresos per capita en México")
```

![](/images/chunk%202.png)<!-- -->




### Adding time by 6 years 
``` r
fit2 <- percapita %>%
  model(trend_model = TSLM(GDP_per_capita ~ trend()))
```

    ## Warning: 7 errors (1 unique) encountered for trend_model
    ## [7] 0 (non-NA) cases

``` r
fit
```

    ## # A mable: 263 x 2
    ## # Key:     Country [263]
    ##    Country             trend_model
    ##    <fct>                   <model>
    ##  1 Afghanistan              <TSLM>
    ##  2 Albania                  <TSLM>
    ##  3 Algeria                  <TSLM>
    ##  4 American Samoa           <TSLM>
    ##  5 Andorra                  <TSLM>
    ##  6 Angola                   <TSLM>
    ##  7 Antigua and Barbuda      <TSLM>
    ##  8 Arab World               <TSLM>
    ##  9 Argentina                <TSLM>
    ## 10 Armenia                  <TSLM>
    ## # ... with 253 more rows




``` r
fit %>% forecast(h = "6 years")
```

    ## # A fable: 1,578 x 5 [1Y]
    ## # Key:     Country, .model [263]
    ##    Country     .model       Year  GDP_per_capita .mean
    ##    <fct>       <chr>       <dbl>          <dist> <dbl>
    ##  1 Afghanistan trend_model  2018    N(526, 9653)  526.
    ##  2 Afghanistan trend_model  2019    N(534, 9689)  534.
    ##  3 Afghanistan trend_model  2020    N(542, 9727)  542.
    ##  4 Afghanistan trend_model  2021    N(550, 9766)  550.
    ##  5 Afghanistan trend_model  2022    N(558, 9806)  558.
    ##  6 Afghanistan trend_model  2023    N(566, 9847)  566.
    ##  7 Albania     trend_model  2018 N(4716, 476419) 4716.
    ##  8 Albania     trend_model  2019 N(4867, 481086) 4867.
    ##  9 Albania     trend_model  2020 N(5018, 486012) 5018.
    ## 10 Albania     trend_model  2021 N(5169, 491198) 5169.
    ## # ... with 1,568 more rows

``` r
fit %>%
  forecast(h = "6 years") %>%
  filter(Country == "Mexico") %>%
  autoplot(percapita) +
  labs(y = "$Pesos", title = "Ingresos per capita en México")
```

![](/images/chunk%203.png)<!-- -->
