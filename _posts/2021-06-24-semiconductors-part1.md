---
layout: post
title: "Semiconductors Quant Analysis"
description: "An Overview to the Semiconductor market"
output: html_document
date: 2021-06-25 19:50:00 -0400
category: r
tags: [data analysis, forecasting, r, finance]
comments: true
---


We know that Semiconductors industry it's a complex industry. Without this industry, We could not be reading this article. We could not imagine all this progress. But understand this monster it's hard.

That's why I created this project.

I'm going to divide the project in 2 parts.

The first part is divided into 4 main points:

* A short introduction about the business model that exist in the industry 
* A comparation about some index's with specially focus on FOX Index 
* Select the companies that we will be analyzing throughout the project
* Create models around the data and plot some nice visualizations

The second part is divided into X points:

* Talk about one companie in particular 
* Select some financial ratios
* Download and plot the data
* Explain patterns 
* Regression analysis and forecasting modeling

For me, the goal of this project consists on show you my knowledge on quant financial analysis, statistical learning and writing.

For you, the project consists on understanding how the industry works, his performance over the years and why not, pick the opportunity to invest in the semiconductor industry.

### Let's begin with a comparation in the performance of some Index's...

![Index](/images/semiconductores/performancecomparation.png)


Above, we have 6 Index

SOX .- PHLX Semiconductor
DJI.- Dow Jones Industrial 
IXIC.- NASDAQ COMPOSITE
GSPC.- S&P 500
DAX.- German Index
TSXV.- S&P/TSX CANADA COMPOSITE INDEX

I'm going to use some packages.-

Tidyquant for finance
Tidyverse for dplyr and ggplot
Fpp3 for forecasting models
Ggthemes for beautiful plots


