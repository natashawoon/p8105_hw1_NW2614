Homework 1
================
Natasha Woon
2026-09-25

# Problem 1

## Load Packages

``` r
library(tidyverse)
```

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.2.1     ✔ readr     2.2.0
    ## ✔ forcats   1.0.1     ✔ stringr   1.6.0
    ## ✔ ggplot2   4.0.3     ✔ tibble    3.3.1
    ## ✔ lubridate 1.9.5     ✔ tidyr     1.3.2
    ## ✔ purrr     1.2.2     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

``` r
data("penguins", package = "palmerpenguins")
```

## Description of Penguins Data set

Write a short description of the penguins dataset (not the penguins_raw
dataset) using inline R code. In your discussion, please include:

the data in this dataset, including names / values of important
variables the size of the dataset (using nrow and ncol) the mean flipper
length

The data in this dataset describes different species of penguins across
different islands. The

This data set has 344 rows and 8 columns.

The mean flipper length is 200.9152047mm.

## Scatterplot

``` r
ggplot(data = penguins,
       mapping = aes(bill_length_mm, flipper_length_mm, color = species)) + geom_point()
```

![](Homework_1_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

``` r
ggsave("scatterplot.png")
```

    ## Saving 7 x 5 in image
