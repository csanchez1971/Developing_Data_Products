Peer-graded assignment - RStudio Presenter
========================================================
author: Carlos Sanchez
date: 19/March/2021
autosize: true

Introduction
========================================================

The current 'RStudio Presenter' presentation will include the following sections:

1. Presentation's cover
2. Summary of the different sections
3. Data loading
4. Some Calculations
5. Plots


Data Loading
========================================================
After loading the dataset `mtcars` we display some summary data: 


```r
data(mtcars); mtcars$cyl <- as.factor(mtcars$cyl); head(mtcars)
```

```
                   mpg cyl disp  hp drat    wt  qsec vs am gear carb
Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4
Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4
Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1
Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1
Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2
Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1
```



Some Calculations
======================================================

Linear regression of qsec (1/4 mile time vs Miles per Gallon)


```r
mod <- lm(mpg ~ qsec, data = mtcars)
summary(mod)
```

```

Call:
lm(formula = mpg ~ qsec, data = mtcars)

Residuals:
    Min      1Q  Median      3Q     Max 
-9.8760 -3.4539 -0.7203  2.2774 11.6491 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)  
(Intercept)  -5.1140    10.0295  -0.510   0.6139  
qsec          1.4121     0.5592   2.525   0.0171 *
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 5.564 on 30 degrees of freedom
Multiple R-squared:  0.1753,	Adjusted R-squared:  0.1478 
F-statistic: 6.377 on 1 and 30 DF,  p-value: 0.01708
```

Plots
========================================================



```r
library(ggplot2)
ggplot(mtcars, aes(x=qsec, y=mpg, color=cyl)) + geom_point() + geom_smooth(method = "lm") + theme_bw()+ ggtitle("'1/4 mile time' vs 'Miles per Gallon'")
```

<img src="RStudioPresenter-figure/plots-1.png" title="plot of chunk plots" alt="plot of chunk plots" style="display: block; margin: auto;" />
