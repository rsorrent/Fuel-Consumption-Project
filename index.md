---
title       : Fuel Consumption for 1974 Cars
subtitle    : An example of prediction
author      : Riccardo Sorrentino
job         : Developing Data Products Coursera Course
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

### An example of prediction

<br>
<br>
<br>
<br>
<br>
<h4> The app is an example of prediction based on the mtcars dataset included in the R Base package. The data was extracted from the 1974 Motor Trend US magazine. It comprises fuel consumption and 10 aspects of automobile features and performance for 32 models sold in 1973-74.
<p>  

---

### The prediction algorithm

<br>
<h4>  It has been performed a linear regression in order to predict the fuel consumption of 1973-74 models, in miles per gallon (mpg in the mtcars dataset) knowing their horsepower (hp in the dataset) and their weight in lb/1000 (wt in the dataset).
<p>  

<h4> The example is for illustrative purpose only. Data is too old to be useful. Moreover, it has a limited analytical value: as a matter of fact weight and hp are correlated.
<p>


```r
data1 <- mtcars
cor(data1$hp, data1$wt)
```

```
## [1] 0.6587479
```

--- .class #id 

### The engine of prediction

<h4>The linear regression has given these results


```r
fit1 <- lm(mpg ~ hp + wt, data = data1)
round(summary(fit1)$coeff, 3)
```

```
##             Estimate Std. Error t value Pr(>|t|)
## (Intercept)   37.227      1.599  23.285    0.000
## hp            -0.032      0.009  -3.519    0.001
## wt            -3.878      0.633  -6.129    0.000
```

<h4>On the basis of these results it has been possible to buind this function in order to calculate the fuel consumption from the data on weight and horsepower given by the app user. 


```r
mpg <- function(hp, wt) 33.22727 - 0.03177*hp - 3.87783*wt
```

--- .class #id

## The design of the app

<br>
<br>
<br>
<br>
<h5>The app has been realized using the Slidify package in R Studio. It has been chosen a numeric input control to input the weight, with an interval of 0.1 lbs, and a text input control and a submit button to input the horsepower. 



