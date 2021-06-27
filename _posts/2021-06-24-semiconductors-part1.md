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

--- 
That's why I created this project. **I'm going to divide the project in 2 parts.** 

> The first part is divided into 4 main points:

* A short introduction about the business model that exist in the industry 
* A comparation about some index's with specially focus on FOX Index 
* Select the companies that we will be analyzing throughout the project
* Create models around the data and plot some nice visualizations

> The second part is divided into X points:

* I'm going to talk about one companie in particular 
* Select some financial ratios
* Download and plot the data
* Explain patterns 
* Regression analysis and forecasting modeling
  

---
> **For me**, the goal of this project consists on show you my knowledge on quant financial analysis, statistical learning and writing.

> **For you**, the project consists on understanding how the industry works, his performance over the years and why not, pick the opportunity to invest in the semiconductor industry.

---
Let's begin with the first main point... **the business models.**

In order to understand the complexity around the industry, we need an overview of the process for creating an IC'S 

![Index](/images/semiconductores/process.png)

*As wee see, there are many steps. But We can categorize the whole process in three major business models.*

![Index](/images/semiconductores/HD.png)

### 1.- Foundry

**Foundry companies are concerned only with IC manufacturing.**

> The foundry model is a microelectronics engineering and manufacturing business model consisting of a semiconductor fabrication plant, or foundry, and an integrated circuit design operation, each belonging to separate companies or subsidiaries.

**Foundry Model it's dominated by TSMC.**

### 2.- IDM

**IDMs design and manufacture integrated circuits (ICs).**

> An integrated device manufacturer (IDM) is a semiconductor company which designs, manufactures, and sells integrated circuit (IC) products. As a classification, IDM is often used to differentiate between a company which handles semiconductor manufacturing in-house, and a fabless semiconductor company, which outsources production to a third-party. Due to the dynamic nature of the semiconductor industry, the term IDM has become less accurate than when it was coined.

**Intel and Texas instruments are examples of this model.**

### 3.- Fabless

###Fabless companies focus only on IC design.

> Fabless manufacturing is the design and sale of hardware devices and semiconductor chips while outsourcing their fabrication (or fab) to a specialized manufacturer called a semiconductor foundry. Foundries are typically, but not exclusively, located in the United States, People's Republic of China, and Taiwan. Fabless companies can benefit from lower capital costs while concentrating their research and development resources on the end market. Some fabless companies and pure play foundries (like TSMC) may offer integrated-circuit design services to third parties.

**Broadcom, Qualcomm and AMD are examples of this model.**


### Let's begin with an index performance comparation... but first

I'm going to use the **PHLX Semiconductor Sector** Index

> PHLX Semiconductor Sector is a Philadelphia Stock Exchange capitalization-weighted index composed of the 30 largest companies primarily involved in the design, distribution, manufacture, and sale of semiconductors. It was created in 1993 by the Philadelphia Stock Exchange

Let's see a comparation between the major index's in USA.

![Index](/images/semiconductores/performancecomparation.png)


* **Blue_SOX.-** PHLX Semiconductor
* **BlueSky_DJI.-** Dow Jones Industrial 
* **Pink_IXIC.-** NASDAQ COMPOSITE
* **Purple_GSPC.-** S&P 500
* **Orange_DAX.-** German Index
* **Yellow_TSXV.-** S&P/TSX CANADA COMPOSITE INDEX

**If we look closely, the PHLX Index outperforms the NASDAQ COMPOSITE which contains companies like Apple, Amazon, Facebook and Alphabet... not bad, right?**

So, for this project i'm going to choose these companies, 2 or 3 for model.

* **Foundry:** TSMC and UMC.
* **IDM’s:** Intel, Texas instruments and NPX
* **Fabless:** Broadcomm, Qualcomm and Nvidia.

Tidyquant for finance
Tidyverse for dplyr and ggplot
Fpp3 for forecasting models
Ggthemes for beautiful plots


