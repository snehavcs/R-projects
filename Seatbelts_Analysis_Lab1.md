---
title: "Seatbelt Analysis"
author: "Sneha Vasanth"
date: "January 10, 2017"
output: html_document
---
#1.Data Cleaning

```r
seatbelts <- read.csv("seatbelts.csv")
class(seatbelts)
```

```
## [1] "data.frame"
```

```r
dim(seatbelts)
```

```
## [1] 192  10
```

How many cases are in the observed data? 
Answer - 192, since there are 192 rows in the dataframe

```r
colnames(seatbelts)
```

```
##  [1] "year.month"    "year"          "DriversKilled" "drivers"      
##  [5] "front"         "rear"          "kms"           "PetrolPrice"  
##  [9] "VanKilled"     "law"
```

Summary

```r
summary(seatbelts)
```

```
##    year.month        year      DriversKilled      drivers    
##  Min.   :1969   Min.   :1969   Min.   : 60.0   Min.   :1057  
##  1st Qu.:1973   1st Qu.:1973   1st Qu.:104.8   1st Qu.:1462  
##  Median :1977   Median :1977   Median :118.5   Median :1631  
##  Mean   :1977   Mean   :1977   Mean   :122.8   Mean   :1670  
##  3rd Qu.:1981   3rd Qu.:1981   3rd Qu.:138.0   3rd Qu.:1851  
##  Max.   :1985   Max.   :1985   Max.   :198.0   Max.   :2654  
##      front             rear            kms         PetrolPrice     
##  Min.   : 426.0   Min.   :224.0   Min.   : 7685   Min.   :0.08118  
##  1st Qu.: 715.5   1st Qu.:344.8   1st Qu.:12685   1st Qu.:0.09258  
##  Median : 828.5   Median :401.5   Median :14987   Median :0.10448  
##  Mean   : 837.2   Mean   :401.2   Mean   :14994   Mean   :0.10362  
##  3rd Qu.: 950.8   3rd Qu.:456.2   3rd Qu.:17203   3rd Qu.:0.11406  
##  Max.   :1299.0   Max.   :646.0   Max.   :21626   Max.   :0.13303  
##    VanKilled           law        
##  Min.   : 2.000   Min.   :0.0000  
##  1st Qu.: 6.000   1st Qu.:0.0000  
##  Median : 8.000   Median :0.0000  
##  Mean   : 9.057   Mean   :0.1198  
##  3rd Qu.:12.000   3rd Qu.:0.0000  
##  Max.   :17.000   Max.   :1.0000
```


what variables are observed for each month?
Answer - numeric

```r
attach(seatbelts)
year.month
```

```
##   [1] 1969.000 1969.083 1969.167 1969.250 1969.333 1969.417 1969.500
##   [8] 1969.583 1969.667 1969.750 1969.833 1969.917 1970.000 1970.083
##  [15] 1970.167 1970.250 1970.333 1970.417 1970.500 1970.583 1970.667
##  [22] 1970.750 1970.833 1970.917 1971.000 1971.083 1971.167 1971.250
##  [29] 1971.333 1971.417 1971.500 1971.583 1971.667 1971.750 1971.833
##  [36] 1971.917 1972.000 1972.083 1972.167 1972.250 1972.333 1972.417
##  [43] 1972.500 1972.583 1972.667 1972.750 1972.833 1972.917 1973.000
##  [50] 1973.083 1973.167 1973.250 1973.333 1973.417 1973.500 1973.583
##  [57] 1973.667 1973.750 1973.833 1973.917 1974.000 1974.083 1974.167
##  [64] 1974.250 1974.333 1974.417 1974.500 1974.583 1974.667 1974.750
##  [71] 1974.833 1974.917 1975.000 1975.083 1975.167 1975.250 1975.333
##  [78] 1975.417 1975.500 1975.583 1975.667 1975.750 1975.833 1975.917
##  [85] 1976.000 1976.083 1976.167 1976.250 1976.333 1976.417 1976.500
##  [92] 1976.583 1976.667 1976.750 1976.833 1976.917 1977.000 1977.083
##  [99] 1977.167 1977.250 1977.333 1977.417 1977.500 1977.583 1977.667
## [106] 1977.750 1977.833 1977.917 1978.000 1978.083 1978.167 1978.250
## [113] 1978.333 1978.417 1978.500 1978.583 1978.667 1978.750 1978.833
## [120] 1978.917 1979.000 1979.083 1979.167 1979.250 1979.333 1979.417
## [127] 1979.500 1979.583 1979.667 1979.750 1979.833 1979.917 1980.000
## [134] 1980.083 1980.167 1980.250 1980.333 1980.417 1980.500 1980.583
## [141] 1980.667 1980.750 1980.833 1980.917 1981.000 1981.083 1981.167
## [148] 1981.250 1981.333 1981.417 1981.500 1981.583 1981.667 1981.750
## [155] 1981.833 1981.917 1982.000 1982.083 1982.167 1982.250 1982.333
## [162] 1982.417 1982.500 1982.583 1982.667 1982.750 1982.833 1982.917
## [169] 1983.000 1983.083 1983.167 1983.250 1983.333 1983.417 1983.500
## [176] 1983.583 1983.667 1983.750 1983.833 1983.917 1984.000 1984.083
## [183] 1984.167 1984.250 1984.333 1984.417 1984.500 1984.583 1984.667
## [190] 1984.750 1984.833 1984.917
```

#2.Computing Averages

We can find the mean age using the mean() function. What is the result? -  122.8021

```r
mean(seatbelts[,"DriversKilled"])
```

```
## [1] 122.8021
```

But is this the mean by year? Or over all years? - It is the mean over all years

Let's subset the data and see:

```r
mean(seatbelts[seatbelts[,"year"]>=1969 &
seatbelts[,"year"]<1970,"DriversKilled"])
```

```
## [1] 103
```

It's not the same as mean by years
Mean by year is given by 

```r
by(seatbelts[,"DriversKilled"], seatbelts[,"year"], mean)
```

```
## seatbelts[, "year"]: 1969
## [1] 103
## -------------------------------------------------------- 
## seatbelts[, "year"]: 1970
## [1] 122.4167
## -------------------------------------------------------- 
## seatbelts[, "year"]: 1971
## [1] 140.0833
## -------------------------------------------------------- 
## seatbelts[, "year"]: 1972
## [1] 145.0833
## -------------------------------------------------------- 
## seatbelts[, "year"]: 1973
## [1] 144.3333
## -------------------------------------------------------- 
## seatbelts[, "year"]: 1974
## [1] 132
## -------------------------------------------------------- 
## seatbelts[, "year"]: 1975
## [1] 125.75
## -------------------------------------------------------- 
## seatbelts[, "year"]: 1976
## [1] 120.9167
## -------------------------------------------------------- 
## seatbelts[, "year"]: 1977
## [1] 116.25
## -------------------------------------------------------- 
## seatbelts[, "year"]: 1978
## [1] 125.5833
## -------------------------------------------------------- 
## seatbelts[, "year"]: 1979
## [1] 125.4167
## -------------------------------------------------------- 
## seatbelts[, "year"]: 1980
## [1] 117.8333
## -------------------------------------------------------- 
## seatbelts[, "year"]: 1981
## [1] 110.5
## -------------------------------------------------------- 
## seatbelts[, "year"]: 1982
## [1] 118.6667
## -------------------------------------------------------- 
## seatbelts[, "year"]: 1983
## [1] 114.25
## -------------------------------------------------------- 
## seatbelts[, "year"]: 1984
## [1] 95.25
## -------------------------------------------------------- 
## seatbelts[, "year"]: 1985
## [1] 118
```

What was the average number of fatalities in 1970? 1978?

```r
mean(seatbelts[seatbelts[,"year"]==1970,"DriversKilled"])
```

```
## [1] 122.4167
```

Answer - In 1970, average number of fatalities was 122.4167


```r
mean(seatbelts[seatbelts[,"year"]==1978,"DriversKilled"])
```

```
## [1] 125.5833
```

Answer - In 1978, average number of fatalities was 125.5833

What was the average number of rear seat fatalities in 1972? 1980?

The average number of rear seat fatalities in 1972 was 440.25

```r
mean(seatbelts[seatbelts[,"year"]==1972,"rear"])
```

```
## [1] 440.25
```

The average number of rear seat fatalities in 1980 was 380.8333

```r
mean(seatbelts[seatbelts[,"year"]==1980,"rear"])
```

```
## [1] 380.8333
```

#3.Exploring Relationships  

Plot the relationship between drivers killed or seriously injured and petrol price and kilometers traveled. 

```r
plot(seatbelts[,"kms"], seatbelts[,"drivers"])
```

![plot of chunk unnamed-chunk-12](figure/unnamed-chunk-12-1.png)


What do you see?

Drivers killed vs the the distance travelled:

There seems to be a negative correlation between the kms travelled and the number of drivers injured.


```r
plot(seatbelts[,"kms"], seatbelts[,"DriversKilled"])
mod1 <- lm(seatbelts[,"DriversKilled"]~seatbelts[,"kms"])
abline(mod1, lwd=2)
```

![plot of chunk unnamed-chunk-13](figure/unnamed-chunk-13-1.png)

Drivers killed vs the petrol price


```r
plot(seatbelts[,"PetrolPrice"], seatbelts[,"DriversKilled"])
mod1 <- lm(seatbelts[,"DriversKilled"] ~ seatbelts[,"PetrolPrice"])
abline(mod1, lwd = 2)
```

![plot of chunk unnamed-chunk-14](figure/unnamed-chunk-14-1.png)


What hypotheses might you make after seeing these relationships?

The evidence suggests that, higher the kms travelled in the car, less likely is the injury/death, i.e. there is a negative association. This can be an indication that inexperienced drivers are more prone to injury/death.

Similarly, there is a negative association between price of petrol and distance travelled.  

#4.Exploring Relationships II

Consider a research question that asks about the implementation of the seatbelt law.

Did it have an effect? Did it reduce fatalities?

```r
plot(seatbelts[,"year"], seatbelts[,"DriversKilled"])
```

![plot of chunk unnamed-chunk-15](figure/unnamed-chunk-15-1.png)


What descriptive and visual tools might we use to explore this? 
Examine the mean fatalities before and after the implementation of the law. Remember to subset your data (hint: there are two variables you can use to do this to do this).

Descriptive analysis

We can identify the mean value of drivers killed by subsetting the data before and after the law was implemented.

```r
mean(seatbelts[seatbelts[,"law"]==0,"DriversKilled"])
```

```
## [1] 125.8698
```

```r
mean(seatbelts[seatbelts[,"law"]==1,"DriversKilled"])
```

```
## [1] 100.2609
```

We can also use dplyr library to group by law and identify the mean value of drivers killed.

```r
library(dplyr)
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
seatbelts %>%
  group_by(law) %>%
   summarise(mean(DriversKilled))
```

```
## # A tibble: 2 × 2
##     law `mean(DriversKilled)`
##   <int>                 <dbl>
## 1     0              125.8698
## 2     1              100.2609
```
The mean value of the number of drivers killed has decreased about 25 points after implementation of the law.

Produce a figure to get some visual intuition about the response to the seatbelt law. 
Was it a gradual decline? Sharp?

```r
plot(seatbelts$year , seatbelts$drivers , col= ifelse(seatbelts$law==0, "red", "blue"))
```

![plot of chunk unnamed-chunk-18](figure/unnamed-chunk-18-1.png)

```r
plot(seatbelts$year.month, seatbelts$DriversKilled , type = 'l',xaxt='n')
axis(side = 1, at = seatbelts$year, labels = TRUE)
abline(v = as.numeric(1983.167))
```

![plot of chunk unnamed-chunk-18](figure/unnamed-chunk-18-2.png)

Mean value of drivers killed per year is plotted against every distinct year to identify the change in the number of drivers killed before and after the law.


```r
mean.yearly <- by(seatbelts[,"DriversKilled"], seatbelts[,"year"], mean)
mean.yearly
class(mean.yearly)
years.factor <- factor(seatbelts$year)
level1 <- levels(years.factor)
l1 <- as.numeric(level1)
l1
plot(l1, mean.yearly,xaxt='n')
axis(side = 1, at = seatbelts$year, labels = TRUE)
abline(v = as.numeric(1983.167))
```

![plot of chunk unnamed-chunk-19](figure/unnamed-chunk-19-1.png)


As per the graph, there seems to be a decline(mean reduces from 125 to 100) in the number of drivers killed immediately after the seatbelt law was implemented, but the number increases over the next few years and gets back to the previous rate. So, overall the decline is gradual.

Does it appear large in magnitude or small?
It appears to be small in magnitude since there is a gradual decline in the number of drivers killed considering the mean value before and after the law was passed.

We can also use ggplot to visualize this

```r
library(ggplot2)
ggplot(seatbelts, aes(x=year.month, y=DriversKilled,col=law))+geom_line()
```

![plot of chunk unnamed-chunk-20](figure/unnamed-chunk-20-1.png)

5. Extra Credit Question: Be creative! What additional research questions might you
want to explore in this data? See what you can discover about the relationships that exist between variables in this dataset. Produce a table or figure to communicate your findings and describe in words what you found and why it's interesting.

Van drivers killed vs the the distance travelled:


```r
plot(seatbelts[,"kms"], seatbelts[,"VanKilled"])
mod1 <- lm(seatbelts[,"VanKilled"]~seatbelts[,"kms"])
abline(mod1, lwd=2)
```

![plot of chunk unnamed-chunk-21](figure/unnamed-chunk-21-1.png)

Van drivers killed vs the petrol price


```r
plot(seatbelts[,"PetrolPrice"], seatbelts[,"VanKilled"])
mod1 <- lm(seatbelts[,"VanKilled"] ~ seatbelts[,"PetrolPrice"])
abline(mod1, lwd = 2)
```

![plot of chunk unnamed-chunk-22](figure/unnamed-chunk-22-1.png)
There seems to be a negative correlation between the kms travelled and the number of van drivers killed. Similarly, there is a negative association between price of petrol and van drivers killed.

Petrol price vs year


```r
plot(seatbelts[,"PetrolPrice"], seatbelts[,"year"])
mod1 <- lm(seatbelts[,"year"] ~ seatbelts[,"PetrolPrice"])
abline(mod1, lwd = 2)
```

![plot of chunk unnamed-chunk-23](figure/unnamed-chunk-23-1.png)

There is an increase in petrol price every year.


