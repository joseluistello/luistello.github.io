---
layout: post
title: "Data Analysis Process"
description: "Titanic And Machine Learning"
output: html_document
date: 2021-07-090 -0400
category: r
tags: [data analysis, machine learning, r, data wrangling]
comments: true
---

### Introduction  

 This project's special. I'm going to talk about the process of analyzing data and *what I hope to accomplish here is to give you my way of thinking about data analysis.* 
 
 ##### **As Sam Hinkie [wrote](https://www.espn.com/pdf/2016/0406/nba_hinkie_redact.pdf) about Seth Klarman and his approach at Baupost Group:** 
> **It isn’t the only way of thinking, but it’s how we approach it.**  


That's it. My way is not exclusive, but it's how I approach it. 

##### A holistic way to see the process

![Index](/images/data%20analysis/Page%201/HD.png)



```{r}
library(tidyverse)
library(ggthemes)
```
```{r}
train <- read.csv("data/train.csv", header = TRUE)
test <- read.csv("data/test.csv", header = TRUE)
```

```{r}
str(train)
```

```{r}
str(test)
```
##### Drop NA values from test set
```{r}
test <- data.frame(test[1], Survived = rep("NA", nrow(test)), test[ , 2:ncol(test)])
```

##### Merge train and test for visualization and analysis

```{r}
data <- rbind(train, test)
```

##### Create file from rbind product
```{r}
write.csv(data, "./data/data.cvs", row.names = FALSE )
```

```{r}
length(data$PassengerId)
```

```{r}
length(unique(data$PassengerId))
```

```{r}
data$Survived <- as.factor(data$Survived)
table(data$Survived, dnn = "Number of Survived in Data Frame")
```

```{r}
prop.table(table(as.factor(train$Survived), dnn = "Survive and death ratio in Train Data"))
```

##### Time to change type of data

```{r}
data$Pclass <- as.factor(data$Pclass)
```


```{r}
table(data$Pclass, dnn = "Pclass values in Data")
```
















---

### Hi! this project it's under construction.


### If you want to see more of my work, check this out:

### 📕 Latest Blog Posts and Projects

<!-- BLOG-POST-LIST:START -->
- [Definiendo el valor y la estructura de precios](https://joseluistello.substack.com/p/valor-y-estructura-de-precios)
- [Estructura de costos](https://joseluistello.substack.com/p/estructura-de-costos)
- [Fijación de precios](https://joseluistello.substack.com/p/fijacin-de-precios)
- [An Introduction to Forecasting Modeling](https://joseluistello.github.io/r/forecasting_mexico_GDPPC/)
- [Semiconductor Market Analysis](https://joseluistello.github.io/r/semiconductors-part1/)

<!-- BLOG-POST-LIST:END -->

## Connect with me:

### [🔥 Substack ](https://joseluistello.substack.com/)
### [✔️ Twitter](https://twitter.com/jotaele_tello)
### [😊 Linkedin](https://www.linkedin.com/in/joseluistello/)
### [📈 Resume](https://www.notion.so/joseluistello/resume-908176d50910492f82bb0c2c50150406)
### [❤️ DataBase](https://www.notion.so/joseluistello/resources-3b96a11183d342b889c95e9bcb1e0c7f)
---

---