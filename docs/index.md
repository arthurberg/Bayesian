--- 
title: "PHS 528: Bayesian Methods"
author: "Arthur Berg"
date: "2022-09-15"
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

## Coins, Urns, and Bags

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


:::{.exercise name="marbles" .prob}
Suppose there’s a bag containing 50 marbles with each marble being either red or yellow. 

(a) Five marbles are randomly selected **with replacement** and each one is found to be yellow. What is the probability all of the marbles in the bag are yellow?

(b) Five marbles are randomly selected **without replacement** and all are found to be yellow. What is the probability all of the marbles in the bag are yellow?
:::

:::{.example #gemstones name="gemstones" .lizi}
Suppose there are $n$ bags labeled $1,\ldots,n$ with bag $i$ containing $i$ rubies and $n-i$ diamonds. Suppose a bag $i$ is selected with probability directly proportional with $i$, and a random gemstone is selected from that bag. What is the probability that it is a diamond? Provide a theoretical calculation and a simulated approximation.
:::


```r
n=13
Pr_given_B=(1:n)/n
Pr_of_B=(1:n)/sum(1:n)
sum(Pr_given_B * Pr_of_B)
[1] 0.6923077
(2*n+1)/(3*n)
[1] 0.6923077

R=10^6 # number of random draws
B=1:n
x1=sample(B,size=R,replace=T,prob=B)
x2=sapply(x1,function(x){rbinom(1,1,prob=x/n)})
mean(x2)  
[1] 0.692364
```

\@ref(exm:gemstones)



