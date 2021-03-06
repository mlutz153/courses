---
title       : Plotting - Math Functions
subtitle    : Computing for Data Analysis
author      : Roger Peng, Associate Professor
job         : Johns Hopkins Bloomberg School of Public Health
logo        : bloomberg_shield.png
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
url:
  lib: ../../libraries
  assets: ../../assets
widgets     : [mathjax]            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
---

## Mathematical Annotation

R can produce LaTeX-like symbols on a plot for mathematical annotation. This is very handy and is useful for making fun of people who use other statistical packages.

- Math symbols are “expressions” in R and need to be wrapped in the `expression` function
- There is a set list of allowed symbols and this is documented in ?plotmath
- Plotting functions that take arguments for text generally allow expressions for math symbols

---

## Mathematical Annotation

Some examples.

```r
plot(0, 0, main = expression(theta == 0),
     ylab = expression(hat(gamma) == 0),
     xlab = expression(sum(x[i] * y[i], i==1, n)))
```

Pasting strings together.

```r
x <- rnorm(100)
hist(x,
     xlab=expression("The mean (" * bar(x) * ") is " *
                     sum(x[i]/n,i==1,n)))
```

---

## Substituting

What if you want to use a computed value in the annotation?

```r
x <- rnorm(100)
y <- x + rnorm(100, sd = 0.5)
plot(x, y,
     xlab=substitute(bar(x) == k, list(k=mean(x))),
     ylab=substitute(bar(y) == k, list(k=mean(y)))
     )
```

Or in a loop of plots

```r
par(mfrow = c(2, 2))
for(i in 1:4) {
        x <- rnorm(100)
        hist(x, main=substitute(theta==num,list(num=i)))
}
```

---

## Summary of Important Help Pages

- ?par
- ?plot 
- ?xyplot 
- ?plotmath 
- ?axis
