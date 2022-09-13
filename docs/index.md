--- 
title: "PHS 528: Bayesian Methods"
author: "Arthur Berg"
date: "2022-09-13"
site: bookdown::bookdown_site
documentclass: book
bibliography: [book.bib, packages.bib]
url: https://bookdown.org/yihui/bookdown
#cover-image: images/cover.jpg
description: 
biblio-style: apalike
csl: chicago-fullnote-bibliography.csl
---

# Fundamentals of Probability

## Binomial Distribution 

:::{.example .lizi}
Consider 100 flips of a fair coin.

(a) What is the probability of observing exactly 50 heads in 100 flips of a fair coin?

(b) What is the probability of observing 50 or more heads?

(c) How many heads would be extreme in the sense that there is less than a 5% chance of observing that many heads or more?
:::


```r
# (a)
dbinom(50,100,prob=1/2)
[1] 0.07958924
# (b)
sum(dbinom(50:100,100,prob=1/2))
[1] 0.5397946
1-pbinom(49,100,prob=1/2)
[1] 0.5397946
pbinom(49,100,prob=1/2,lower.tail=FALSE)
[1] 0.5397946
# (c)
qbinom(.95,100,prob=1/2)
[1] 58
qbinom(.05,100,prob=1/2,lower.tail=FALSE)
[1] 58
1-pbinom(57,100,prob=1/2)
[1] 0.06660531
1-pbinom(58,100,prob=1/2)
[1] 0.04431304
```

:::{.example .lizi}
Suppose there’s a bag containing four marbles (弹珠) of which $n$ are blue and $4-n$ are white. What is the probability of drawing blue-white-blue if the marbles are replaced each time? 
:::


```r
n=0:4 #blue
prob=dbinom(2,3,n/4)
prob
[1] 0.000000 0.140625 0.375000 0.421875 0.000000
prob/sum(prob)
[1] 0.00 0.15 0.40 0.45 0.00
```


:::{.exercise .prob}
Suppose five dice are rolled (掷五个骰子). What is the probability three or more sixes are rolled? 
:::



:::{.exercise .prob}
Suppose there’s a bag containing 50 marbles with each marble being either red or yellow. Five marbles are randomly selected **with replacement** and each one is found to be yellow. What is the probability all of the marbles in the bag are yellow?
:::







